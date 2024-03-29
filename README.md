# Video Web Component [![CircleCI](https://circleci.com/gh/Rise-Vision/rise-video/tree/master.svg?style=svg)](https://circleci.com/gh/Rise-Vision/rise-video/tree/master)

## Introduction

`rise-video` is a Polymer 3 Web Component that retrieves video files from Rise Local Storage, and runs them.

Instructions for demo page here:
https://github.com/Rise-Vision/rise-video/blob/master/demo/README.md

## Usage

The below illustrates simple usage of the component.

There is no need to configure listeners if the component runs as editable ( default operation mode ). See the demo section in this repo for a full working example of an HTML page using the component which will illustrate required imports in the `<head>` of the page.

### Example

```
  <body>
    <div id="video-sample-container">
      <rise-video
        id="rise-video-sample"
        files="risemedialibrary-abc123/file1.mp4|risemedialibrary-abc123/file2.webm">
      </rise-video>
    </div>
...

  </body>
```

### Labels

The component may define a 'label' attribute that defines the text that will appear for this instance in the template editor.

This attribute holds a literal value, for example:

```
  <rise-video id="rise-video-sample"
    label="Sample"
    files="risemedialibrary-abc123/welcome.mp4">
  </rise-video>
```

If it's not set, the label for the component defaults to "Video", which is applied via the   [generate_blueprint.js](https://github.com/Rise-Vision/html-template-library/blob/master/generate_blueprint.js) file for a HTML Template build/deployment.

### Attributes

This component receives the following list of attributes:

- **id**: ( string / required ): Unique HTML id with format 'rise-video-<NAME_OR_NUMBER>'.
- **label**: ( string ): An optional label key for the text that will appear in the template editor. See 'Labels' section above.
- **files** ( string / required ): List of video file paths separated by pipe symbol. A file path must be a valid GCS file path. A folder path will not be valid. For example, this is a default file path from Rise Storage:
https://storage.googleapis.com/risemedialibrary-7fa5ee92-7deb-450b-a8d5-e5ed648c575f/Template%20Library/Global%20Assets/welcome.mp4.
To create a valid GCS path, remove *https://storage.googleapis.com/* and replace *%20* with a space.
The resulting GCS path is: risemedialibrary-7fa5ee92-7deb-450b-a8d5-e5ed648c575f/Template Library/Global Assets/welcome.mp4.
- **non-editable**: ( empty / optional ): If present, it indicates this component is not available for customization in the template editor.

### Events

The component sends the following events:

- **_configured_**: The component has initialized what it requires to and is ready to handle a _start_ event.
- **_video-error_**: Thrown if an error during the processing of the files happen. The template does not need to handle this, as the component is already logging errors to BQ when running on a display. Provides an object with the following properties: file, errorMessage and errorDetail.

The component is listening for the following events:

- **_start_**: This event will initiate accessing the video. It can be dispatched on the component when _configured_ event has been fired as that event indicates the component has initialized what it requires to and is ready to watch video files.

### Logs to BQ

The component may log the following:

- **_video-start_** ( info ): The component receives the _start_ event and commences execution.
- TBD...

In every case of an error, examine event-details entry and the other event fields for more information about the problem.

## Built With
- [Polymer 3](https://www.polymer-project.org/)
- [Polymer CLI](https://github.com/Polymer/tools/tree/master/packages/cli)
- [WebComponents Polyfill](https://www.webcomponents.org/polyfills/)
- [npm](https://www.npmjs.org)

## Development

### Local Development Build
Clone this repo and change into this project directory.

Execute the following commands in Terminal:

```
npm install
npm install -g polymer-cli@1.9.7
npm run build
```

**Note**: If EPERM errors occur then install polymer-cli using the `--unsafe-perm` flag ( `npm install -g polymer-cli@1.9.7 --unsafe-perm` ) and/or using sudo.

### Testing
You can run the suite of tests either by command terminal or interactive via Chrome browser.

#### Command Terminal
Execute the following command in Terminal to run tests:

```
npm run test
```

#### Local Server
Run the following command in Terminal: `polymer serve`.

Now in your browser, navigate to:

```
http://127.0.0.1:8081/components/rise-video/test/index.html
```
You can also run a specific test page by targeting the page directly, for example:

```
http://127.0.0.1:8081/components/rise-video/test/unit/rise-video.html
```

## Submitting Issues
If you encounter problems or find defects we really want to hear about them. If you could take the time to add them as issues to this Repository it would be most appreciated. When reporting issues, please use the following format where applicable:

**Reproduction Steps**

1. did this
2. then that
3. followed by this (screenshots / video captures always help)

**Expected Results**

What you expected to happen.

**Actual Results**

What actually happened. (screenshots / video captures always help)

## Contributing
All contributions are greatly appreciated and welcome! If you would first like to sound out your contribution ideas, please post your thoughts to our [community](https://help.risevision.com/hc/en-us/community/topics), otherwise submit a pull request and we will do our best to incorporate it. Please be sure to submit test cases with your code changes where appropriate.

## Resources
If you have any questions or problems, please don't hesitate to join our lively and responsive [community](https://help.risevision.com/hc/en-us/community/topics).

If you are looking for help with Rise Vision, please see [Help Center](https://help.risevision.com/hc/en-us).

**Facilitator**

[Santiago Arriaga Noguez](https://github.com/santiagonoguez "Santiago Arriaga Noguez")
