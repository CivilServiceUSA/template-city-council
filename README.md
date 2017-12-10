![Civil Services Logo](https://raw.githubusercontent.com/CivilServiceUSA/api/master/docs/img/logo.png "Civil Services Logo")

__Civil Services__ is a collection of tools that make it possible for citizens to be a part of what is happening in their Local, State & Federal Governments.

[![Donate](https://cdn.civil.services/donate-button.png)](https://www.paypal.me/civilservices)


DEVELOPERS
===

See **[DEVELOPERS.md](DEVELOPERS.md)** for details on using this repository.  This template, including the rest of the README below, assumes you are starting a new project from scratch, and will be using this template as a base for a new City Council.

**NOTE:**  This project provides no actual data and should ONLY be used as a template for creating new City Council Repositories.

City Council Data for __CITY_NAME__, __STATE_CODE__
===

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg?style=flat)](https://raw.githubusercontent.com/CivilServiceUSA/__REPO_NAME__/master/LICENSE)  [![GitHub contributors](https://img.shields.io/github/contributors/CivilServiceUSA/__REPO_NAME__.svg)](https://github.com/CivilServiceUSA/__REPO_NAME__/graphs/contributors)

![__CITY_NAME__, __STATE_CODE__](city-council/images/backgrounds/640x360/city.jpg "__CITY_NAME__, __STATE_CODE__")


Introduction
---

This project provides the City Council Data, Headshots & City Photo for __CITY_NAME__, __STATE_CODE__ ( JSON, XML, CSV, SQL & YML formats ).  See [Provided Data](#provided-data) below for full list of data in this project.


Completed Tasks
---

We have completed the following Data Collection for __CITY_NAME__, __STATE_CODE__. [Watch Project](https://github.com/CivilServiceUSA/__REPO_NAME__/subscription) to be notified of updates.

- [ ] City Council Data Created
- [ ] City Photo Created
- [ ] Councilor Headshots Created
- [ ] Images Uploaded to CDN
- [ ] GeoJSON File Created
- [ ] Published NPM Package


Maintaining Data
---

This City Council Data is maintained in a Google Spreadsheet.  This data can be updated by the general public, and we will be notified when any change occurs.  So, if you see something wrong, just go ahead and fix it and we'll get a notice of the change.

You will want to use [__CITY_NAME__'s Official City Council Website](__CITY_WEBSITE__) to populate this data. However, they may not have 100% of what we collect, so Google is your friend there :)

### [☑ Manage City Council Data](__CITY_DATA_URL__)


Provided Data
---

Parameter             | Type   | Description
----------------------|--------|----------------
`state_code`          | string | Two Letter State Abbreviation
`city_name`           | string | Name of City
`city_slug`           | string | Name of City converted to lowercase letters and spaces replaced with dashes
`city_population`     | string | Population of City
`city_website`        | string | Official Website of City
`city_background_url` | string | Creative Commons Image you can use for City
`public_records`      | string | URL to Public Records ( not always available )
`latitude`            | string | GPS Latitude of City
`longitude`           | string | GPS Longitude of City
`district`            | string | District of Councilor ( not always available )
`at_large`            | string | At-Large of Councilor ( not always available )
`name`                | string | Full Name of Councilor
`name_slug`           | string | Full Name of Councilor converted to lowercase letters and spaces replaced with dashes
`first_name`          | string | First Name of Councilor
`last_name`           | string | Last Name of Councilor
`gender`              | enum   | Gender of Councilor
`ethnicity`           | enum   | Ethnicity of Councilor
`date_of_birth`       | string | Date of Birth of Councilor
`title`               | enum   | Title of Councilor
`party`               | enum   | Political Party of Councilor
`email`               | string | Work Email Address of Councilor
`phone`               | string | Work Phone Number of Councilor
`address`             | string | Work Mailing Address of Councilor
`twitter_url`         | string | Twitter URL of Councilor ( not always available )
`facebook_url`        | string | Facebook URL of Councilor ( not always available )
`photo_url`           | string | Photo URL of Councilor ( not always available )

* `city_background_url` is available in the following sizes: 640x360, 960x540, 1280x720 & 1920x1080 ( defaults to 1280x720 )
* `city_photo_url` is available in the following sizes: 64x64, 128x128, 256x256, 512x512 & 1024x1024 ( defaults to 512x512 )
