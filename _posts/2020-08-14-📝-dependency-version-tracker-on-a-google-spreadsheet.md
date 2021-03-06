---
layout: post
title: 📝 Dependency version tracker on a Google spreadsheet
summary: Track NPM and Pypi versions of GitHub projects on a Google Spreadsheet
date: 2020-08-14T20:11:49.509Z
---
**TL;DR** [This script](https://gist.github.com/tbille/7b859620b697b1209d321b7e231273ad) grabs the latest version of a list of npm and PyPi packages and compares the latest version to a list of projects that use those packages all that on [a spreadsheet](https://docs.google.com/spreadsheets/d/1WYAgoY8svKtYLr2lN-fIjhZAESUuhQXgUdu-UY64kv8/edit#gid=0).

In my work I manage a lot of GitHub repositories that share the same [npm](https://www.npmjs.com/) and [PyPi](https://pypi.org/) dependencies that we also write. Thanks to [renovate](https://renovate.whitesourcesoftware.com/) we can make sure that we always use the latest versions of those packages. But it happens that we forget some pull requests generated by renovate and leave those dependencies not updated.

To improve this situation I wrote a [simple Google Script](https://gist.github.com/tbille/7b859620b697b1209d321b7e231273ad) that does a few things:

* It pulls the latest version of the npm and PyPi packages that I define
* It pulls the `package.json` and the `requirements.txt` of the listed projects
* It feeds all this data into a Google Spreadsheet

This script runs every hours to update all the package versions. 

The only manual step is to change those variables in case I want to add a package:

```
var SHEET_NAME = "Version tracker"
var SITES_RANGE = "A:A";
var PYPI_RANGE = "B1:D2";
var NPM_RANGE = "E1:G2";
```

After some colours and conditional formating tweaks, it allows me to have a quick overview of the versions that are used in the repositories that I am watching.

![Spreadsheet example](/assets/uploads/screenshot-from-2020-08-14-22-03-23.png "Spreadsheet example")

This gives me a visual overview of the status of the repositories and can estimate rapidly how up to date our repositories are.

The [sheet example](https://docs.google.com/spreadsheets/d/1WYAgoY8svKtYLr2lN-fIjhZAESUuhQXgUdu-UY64kv8/edit?usp=sharing) is publicly available and the script is available on [gist](https://gist.github.com/tbille/7b859620b697b1209d321b7e231273ad).