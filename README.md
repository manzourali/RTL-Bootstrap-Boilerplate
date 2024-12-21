# RTL Bootstrap Boilerplate

This guide explains how to set up and use a workflow to compile SCSS files for Bootstrap (5.3) and automatically generate a minified RTL CSS file.

## Prerequisites

Ensure you have the following installed on your system:

- Node.js and npm
- A package manager (npm or yarn)
- Basic knowledge of SCSS and command-line tools

## Installation

1\. Install Required Packages

Run the following command to install all required dependencies:

```console
npm install sass postcss postcss-cli postcss-rtl autoprefixer cssnano chokidar-cli
```

2\. Project Structure

Set up your project with the following structure:

```bash
assets/
  scss/
    custom.scss
    _variables.scss
    _mixins.scss
  css/
    custom-rtl.min.css (output file)
```

## Configuration

1\. PostCSS Configuration
Create a file named postcss.config.js in the root of your project with the following content:

```console
module.exports = {
  plugins: {
    'postcss-rtl': {},    // Convert LTR to RTL
    autoprefixer: {},     // Add browser-specific prefixes
    cssnano: {            // Minify the output
      preset: 'default'
    }
  }
};
```

2\. Custom Bootstrap SCSS File
change your Bootstrap variables in

```bash
assets
  scss
    bootstrap.scss
```

## Scripts

Update your package.json to include the following scripts:

```console
"scripts": {
  "build:rtl": "sass assets/scss/style.scss | postcss --use postcss-rtl --use cssnano --output assets/css/style.min.css",
  "watch": "chokidar 'assets/scss/**/*.scss' -c 'npm run build:rtl'"
}
```

**Script Descriptions**

- build:rtl: Compiles SCSS to CSS, converts it to RTL, and minifies the output.
- watch: Watches for changes in the assets/scss folder and runs build:rtl automatically.

## Usage

1\. Run the Build Script To manually compile and minify the RTL CSS file, run:

```console
npm run build:rtl
```

2\. Watch for Changes To automatically recompile on SCSS changes, run:

```console
npm run watch
```

3\. Include the CSS FileAdd the generated style.min.css file to your HTML:

```console
<link rel="stylesheet" href="assets/css/style.min.css">
```

## Features

- Light/Dark/System Prefer Mode
- Auto Dark Mode Script
- Form Validation Initialization
- Typography Setup
