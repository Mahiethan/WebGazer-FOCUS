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

`webgazer.js` is being used as an import in the front-end React components. Therefore, the line `export default webgazer;` is required to be added to the end of the file. **This has to be done every time `npm run build` is run to generate a new `webgazer.js` file**.

Copy these two files into the [`./focus-app/src/webgazer`](https://github.com/anaya-s/FOCUS-frontend/tree/main/focus-app/src/webgazer)  folder of the front-end code, to update the Webgazer library import used by the application. To run a local development build of the front-end code, follow the [`README.md`](https://github.com/anaya-s/FOCUS-frontend/blob/main/README.md) file contained inside that repository.

## Modifications to the source code

The original source code has been extensively customised to meet the specific needs of the FOCUS web application. This includes enhancements to existing functions, the creation of new functions, and various bug fixes.

### Modified functions

#### `index.mjs`

- `getPupilFeatures()` - made asynchronous
- `paintCurrentFrame()` - made asynchronous
- `loop()`
    - Limited rate for calculating gaze predictions
    - Removed time calculation (no longer needed for new callback function)
    - Uses new callback function to create video frames, using the `videoElementCanvas` as an argument
    - No longer performs smoothing across most recent four predictions, due to performance issues - this is now done by the modified Kalman filter (see ``)
    - Shows or hide gaze dot based on selected reading mode (see `hideGazeDot()`)
- `init()` - made asynchronous, and introduced new boolean parameter, `recordMouse` to turn on/off mouse event listeners (mouse clicks and movements)
    - This boolean is set to `true` when calibration is performed and mouse clicks/movements are recorded for the regression model, otherwise set to `false` to not record any new data.

- `webgazer.begin()` - introduced new boolean parameter, `recordMouse`, which is used by `init()` to turn on mouse event listeners for calibration
    - `webgazer.begin(true)` is used for calibration
    - `webgazer.begin(false)` is used for reading page to provide frames and gaze predictions

- `webgazer.end()` - uses the existing public variable `paused` to correctly end the Webgazer instance, clear the stream and end usage of webcam.

#### `facemesh.mjs`

- `getEyePatches()` - created a single function `getEyeData()` which uses one single 2D `context` variable to obtain left and right eye data, instead of creating two separate `context` variables for each eye.
    - This aims to reduce memory usage, and improve performance with the use of the `{ willReadFrequently: true }` flag.

<!-- #### `ridgeWeightedReg.mjs`

- `predict()` - make gaze predictions asynchronous for this type of regression model used in the front-end app (weighted ridge) -->

#### `util_regression.mjs`

- `InitRegression()` - applies changes to parameters used by Kalman filter

### New functions

#### `index.mjs`

- `webgazer.getRegressionData()` - new public function to obtain the current calibration data (regression data) if it exists

- `webgazer.setRegressionData()` - new public function to set new calibration data to the regression model

- `stopCalibration()` - new public function used in the calibration page to stop mouse clicks/movements from being recorded temporarily, without using `webgazer.end()`.

- `hideGazeDot()` - new public function used to hide the gaze dot based on the currently selected reading mode.
    - Makes use of a new public variable `showGazeDot` which is set to `true` when reading mode 4 (line-by-line unblurring) is currently selected.

### Bug fixes & additional changes

#### `util_regression.mjs`

- `setData()` - applied fix in this function when setting new calibration data. This was part of a closed issue from the original Webgazer repository, found at https://github.com/brownhci/WebGazer/issues/106, which is still not part of the main source or compiled code. 

#### `params.mjs`

- `params.camConstraints` - the `audio` property inside the `camConstaints` parameter was not originally specified, which means that by default, it is set to `false`. It is now manually set to `false` to ensure that audio is not recorded during the webcam stream, as it is not required.

#### `package.json`

- Installed new `rimraf` package in order to run `npm run build` to generate the necessary `webgazer.js` and `webgazer.js.map` files for the front-end.

A more detailed discussion and justification of these modifications can be found in the included report titled `Webgazer Implementation`, which was created as part of the project's Design Evidence Portfolio.

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