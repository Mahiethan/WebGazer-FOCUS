# Modified Webgazer.js Library for FOCUS Web Application - ES410 Group Project

This project is a modified version of the Webgazer.js library for use with the web application FOCUS: a website to enhance reading productivity, improve attention, and reduce eye strain. This application is part of 2024/25 Group 18's ES410 Group Project at the University of Warwick.

The front-end code which uses this modified library is linked below:

https://github.com/anaya-s/FOCUS-frontend

The original repository which this was forked from is linked below:

https://github.com/brownhci/WebGazer

## How to use?

### Pre-requisites:

- [**Node.js**](https://nodejs.org/en/) - Most up-to-date version recommended

The front-end React application stores this up-to-date `webgazer.js` file inside the [`./focus-app/src/webgazer`](https://github.com/anaya-s/FOCUS-frontend/tree/main/focus-app/src/webgazer)  folder.

After applying any changes to the code, run the command `npm run build` at the root directory to create two files: `webgazer.js` and `webgazer.js.map`. These files are generated inside the `./dist` folder within this repository.

Copy these two files into the [`./focus-app/src/webgazer`](https://github.com/anaya-s/FOCUS-frontend/tree/main/focus-app/src/webgazer)  folder of the front-end code, to update the Webgazer library import used by the application. To run a local development build of the front-end code, follow the [`README.md`](https://github.com/anaya-s/FOCUS-frontend/blob/main/README.md) file contained inside that repository.

## Modifications to the source code

The original source code has been extensively customised to meet the specific needs of the FOCUS web application. This includes enhancements to existing functions, the creation of new functions, and various bug fixes.

A more detailed discussion and justification of these modifications can be found in the included report titled `Webgazer Implementation`, which was created as part of the project's Design Portfolio.

## License

The modifications to the Webgazer.js library are distributed under the same license as the original Webgazer.js library.

### Original License

WebGazer.js - Scalable browser-based webcam eye tracking

Copyright (C) 2016 Brown WebGazer Team

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program. If not, see [GNU Licenses](http://www.gnu.org/licenses/).

### Modifications License

The modifications made to the Webgazer.js library for the FOCUS project also follow the GNU General Public License (GPL) version 3 or later.