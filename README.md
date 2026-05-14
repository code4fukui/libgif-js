# libgif-js

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

A lightweight JavaScript library to parse local GIF files in the browser and extract metadata like dimensions, duration, and frame count.

This project is a fork of the excellent [jsgif](https://github.com/shachaf/jsgif) project, refactored to focus on parsing and metadata extraction.

## Features

-   **Client-Side Parsing:** Processes GIF files directly in the browser—no server-side code needed.
-   **Metadata Extraction:** Retrieves width, height, aspect ratio, total duration, and frame count.
-   **Promise-Based API:** Asynchronous and easy to integrate.
-   **ES Module:** Easily importable into modern JavaScript projects.

## Demo

A demonstration is included in `example.html`. To run it:

1.  Clone this repository.
2.  Serve the project directory from a local web server.
3.  Open `example.html` in your browser (e.g., `http://localhost/example.html`).

**Note:** The example will not work if you open the HTML file directly from your local disk (`file://...`) due to browser security restrictions.

## Installation

Install the package from npm:

```bash
npm install gif-decode
```

## Usage

Import the `readLocalGIF` function and pass it a `File` object, typically from a file input.

```javascript
import readLocalGIF from 'gif-decode';

const fileInput = document.querySelector('input[type="file"]');

fileInput.addEventListener('change', (event) => {
  const file = event.target.files[0];
  if (file) {
    readLocalGIF(file).then((gifInfo) => {
      console.log(gifInfo);
      // Example output:
      // {
      //   width: 500,
      //   height: 375,
      //   ratio: 1.3333333333333333,
      //   duration: 2500,
      //   length: 25
      // }
    });
  }
});
```

## API

### `readLocalGIF(file)`

Returns a `Promise` that resolves with an object containing the GIF's metadata.

-   **`file`**: A `File` object representing the GIF file.

#### Resolved Object Properties

-   `width` (Number): The width of the GIF in pixels.
-   `height` (Number): The height of the GIF in pixels.
-   `ratio` (Number): The aspect ratio of the GIF (`width / height`).
-   `duration` (Number): The total animation duration in milliseconds.
-   `length` (Number): The total number of frames in the GIF.

## License

MIT License — see [LICENSE](LICENSE).