# ui-rs-schedule

`ui-rs-schedule` is a component for creating a customizable scheduler component for your application, e.g. to show events on a timeline. It is provided as a [custom element](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Custom_Elements) for easy integration into your projects.

> If your browser does *NOT* support *custom elements* natively (see [caniuse](http://caniuse.com/#feat=custom-elements)) you have to install the [web components shim](http://webcomponents.org/) and include it in your project before including this component!

The component is part of the [RedsiftUI](https://github.com/redsift/redsift-ui) library. For a documentation of the hero unit see the [official RedsiftUI documentation](https://docs.redsift.io/docs/client-code-redsift-ui).

## Builds

[![Circle CI](https://circleci.com/gh/Redsift/ui-rs-schedule.svg?style=svg)](https://circleci.com/gh/Redsift/ui-rs-schedule)

A UMD build is available from //static.redsift.io/reusable/ui-rs-schedule/latest/ui-rs-schedule.umd-es2015.min.js.

To build locally checkout this repository and

```bash
> cd ui-rs-schedule
> npm install
> npm run build
```

This will create a `./dist` folder with the Javascript and CSS files.

## Browser Usage

Include the Javascript on the bottom of the `<body>`:

```html
<script src="https://d3js.org/d3.v4.0.0-alpha.35.js"></script>
<script src="//static.redsift.io/reusable/ui-rs-schedule/latest/js/ui-rs-schedule.umd-es2015.min.js"></script>
```

Including the Javascript already registers the custom element `rs-schedule` with the browser. Make sure to include [D3v4](https://d3js.org/) *before* the component, as it depends on it!

Use the following HTML code to create a `rs-schedule` element:

```html
<rs-schedule></rs-schedule>
```

Data is added to the chart via Javascript in the following form:

```Javascript
var data = [
    {
        "start": Date.parse("2016-04-13T14:30:00+01:00")
    },
    {
        "end": Date.parse("2016-04-13T18:30:00+01:00")
    },
    {
        "status":"confirmed",
        "summary": "Confirmed overlap event",
        "self": true,
        "start": Date.parse("2016-04-13T16:30:00+01:00"),
        "end": Date.parse("2016-04-13T18:30:00+01:00")
    },
    {
        "status":"tentative",
        "summary": "Tentative event",
        "self": false,
        "start": Date.parse("2016-04-13T15:00:00+01:00"),
        "end": Date.parse("2016-04-13T16:00:00+01:00")
    },
    {
        "status":"proposed",
        "summary": "Suggested event of some significant length",
        "self": false,
        "start": Date.parse("2016-04-13T16:00:00+01:00"),
        "end": Date.parse("2016-04-13T17:00:00+01:00")
    },
];

var chart = document.querySelector('rs-schedule');
chart.width = 600;
chart.data = data;
```

#### CAUTION:

If your browser does not support *custom elements* (and only then!) make sure to wrap the above code into the following code:

```javascript
window.addEventListener('WebComponentsReady', function(e) {
  // setup code ...
});
```

See a description of why this is necessary [here](https://www.polymer-project.org/1.0/docs/migration.html#polymer-ready).

# Development Setup

For development run

```bash
> npm run serve
```

within the repository folder. It will start a web server serving the content of `./samples` and supports live-reloading when a source file is changed.
