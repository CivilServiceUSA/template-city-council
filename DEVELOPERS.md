![Civil Services Logo](https://raw.githubusercontent.com/CivilServiceUSA/api/master/docs/img/logo.png "Civil Services Logo")

City Council Template Usage
===

Introduction
---

Our **[City Council Template](https://github.com/CivilServiceUSA/template-city-council)** is used as a base for getting City Council Data ported over from our [Google Docs](https://docs.google.com/document/d/1lyIqha68D3RgyoVzP5-5A42FiWv-_Tv4wh4rl88z4TM/edit?usp=sharing) into working Repositories in Github.


Requirements
---

- [Node 6.x+](https://nodejs.org/en/)
- [Imagemagick](https://www.imagemagick.org)

**MacOS Easy Install via Brew:**

```
brew install node
brew install imagemagick
brew install graphicsmagick
```


Step #1: Downloading CSV Data
---

Before we can get started, we will want to download the City Council's specific CSV file that was created by our volunteers.

1. Visit Our [City Council Data](https://docs.google.com/document/d/1lyIqha68D3RgyoVzP5-5A42FiWv-_Tv4wh4rl88z4TM/edit?usp=sharing)
2. Scroll to Page 2 and find the first city under the `GITHUB` column that is not colored green
3. Click the `VIEW` link in the `DATA` column for that city
4. Export that CSV file
5. Rename CSV file `city-council-data.csv`


Step #2: Setting up Github Repo
---

Now that we have the CSV file for the city we want to work on, we need to get a Github repo setup for it.  We have already setup repos for some of the cities, but this template can be used with or without our existing repos.

1. Go back to [City Council Data](https://docs.google.com/document/d/1lyIqha68D3RgyoVzP5-5A42FiWv-_Tv4wh4rl88z4TM/edit?usp=sharing) and go to the same city you were working on above.
2. Click the `VIEW` link under the `GITHUB` column ( link should be light grey, if it's green, this city is complete )
3. Either fork this repo on your own Github Account, of if you are a Civil Services contributor, just make a new local branch. If the repo is empty (only contains a README file) copy all the files from our [City Council Template](https://github.com/CivilServiceUSA/template-city-council) into this repo, making sure to also include the hidden files ( files with . in front of them)
4. With the repo cloned locally, run `npm install` to install the projects dependencies ( making sure to read the README Developer Requirements for `imagemagick` and `graphicsmagick` )
5. With the repo cloned locally, move the `city-council-data.csv` file we created earlier into the `./source` folder so it exists at `./source/city-council-data.csv`


Step #3: Updating Template Variables
---

We have setup the following variables so you can do a project wide find and replace.  Before you run any NPM scripts to convert the data, you should do a project wide Find & Replace for the following `KEYORD`.

KEYWORD           | DESCRIPTION
------------------|---------------
`CITY_NAME`       | City Name, e.g. `St. Louis`
`CITY_NAME_SLUG`  | Slug version of the City Name `st-louis` ( all lowercase alphanumberic letters, spaces converted to dashes )
`CITY_DATA_URL`   | Absolute URL to the Civil Services Spreadsheet for the CSV file
`CITY_WEBSITE`    | Absolute URL to the Cities Official City Government Website
`REPO_NAME`       | This is the CivilServiceUSA repo name for this city, e.g. `city-council-ca-san-francisco`
`STATE_CODE`      | Uppercase Two letter abbreviation for the State
`STATE_CODE_SLUG` | Lowercase Two letter abbreviation for the State


Step #4: Building Initial Data
---

We have a few NPM scripts setup to automate most of the build processes.  Once you've updated the Template Variables, we can build out our initial data.

1. Open up terminal and change into your current city council project repo
2. Run `npm run convert-csv` with the newly download CSV file ( this will create a new CSV file with some new columns we need for other data formats )
3. Run `npm run build-data` to build XML, YML, SQL & JSON files
4.


Step #5: Add GeoJSON Data
---

In order for the Civil Services API to use this City Council data, we need to map each district using GeoJSON data.  This allows our API to use an individuals physical location to determine which City Council might represent them.  This process is one of the more difficult to complete as it can be challenging to actually track down a City Council's District Map.

1. Find the most recent GeoJSON file that represents the City Council Districts. There are tools that convert Shape Files to GeoJSON.
2. Verify that the GeoJSON district map file is valid, by opening the file in http://geojson.io.  If the map fails to load there, then our API will not be able to use the file.
3. Once the GeoJSON file is valid, save it to `./source/city-council.geojson`.
4. Open `./source/city-council.geojson` and update each district with a custom ID added to it that must match the district that is named in the CSV file. Each `Feature` in the `FeatureCollection` will need a custom param like `"district": "1"`.  See our [San Francisco](https://raw.githubusercontent.com/CivilServiceUSA/city-council-ca-san-francisco/master/source/city-council.geojson) file as an example.
5. Once the GeoJSON is ready, merge in the City Council data as properties on the GeoJSON so each district has that councilors data `npm run build-geojson`


OPTIONAL: Add Headshots
---

This is another process that takes a crazy long time.  Civil Services wishes to find images for each individual that make them seem friendly and approachable.  We also have a standard we set with image size.  Each image for a headshot is 1024x1024 pixels in size.  We have taken the time to make sure each image we create has the individuals head facing forward and centered within the square.  We also leave a little bit of padding around the individuals face to make sure that these images can be used by designers in either square or circle representations.  If you choose to make these images, here are the requirements:

1. Find and download a High Resolution Images for each City Councilor
2. Use a Photo Editor ( [https://pixlr.com/editor/](https://pixlr.com/editor/) if you do not already have one ) and make the headshot exactly 1024px x 1024px in size
3. Export image with a name like `firstname-lastname.jpg` ( using their actual first and last name, all lower case letters, using only letters a-z and replace all spaces with dashes ).
4. Move the newly create file into this `./source/headshots/` directory
5. Once all headshots are made, run `npm run build-images`


Possible Build Issues
---

The following are a list of known issues.  If you run into an error that is not listed below, please contact us to let us know.

* **ERROR:** `Missing ./source/city-council-data.csv` - This happens when there is no `city-council-data.csv` file in the `./source` directory as it is required for the `npm run convert-csv` process.
