
# thispersondoesnotexist-js

[![NPM version](https://badge.fury.io/js/thispersondoesnotexist-js.svg)](https://npmjs.org/package/thispersondoesnotexist-js) [![Build Status](https://travis-ci.org/kevoj/thispersondoesnotexist-js.svg?branch=master)](https://travis-ci.org/kevoj/thispersondoesnotexist-js) [![GitHub license](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](https://raw.githubusercontent.com/kevoj/thispersondoesnotexist-js/master/LICENSE)

> Api for thispersondoesnotexist.com

StyleGAN is a groundbreaking paper that not only produces high-quality and realistic images but also allows for superior control and understanding of generated images, making it even easier than before to generate believable fake images. The techniques presented in StyleGAN, especially the Mapping Network and the Adaptive Normalization (AdaIN), will likely be the basis for many future innovations in GANs.

## Installation

Npm

```bash
npm install thispersondoesnotexist-js --save
```

Yarn

```bash
yarn add thispersondoesnotexist-js
```

## Usage

```javascript

import ThisPersonDoesNotExist from 'thispersondoesnotexist-js';

const dnte = new ThisPersonDoesNotExist();

dnte.getImage().then(res  => {
	console.log('result->', res);
}).catch(err  => {
	console.log('error->', err);
});

```
### Method getImage({options})

```javascript

dnte.getImage({
	width: 256, // width of the image (default 128)
	height: 256, // high of the image (default 128)
	type: 'file',  // Type of file to generate (file or base64) (default file)
	path: 'avatars' // Path to save (Applies to type file) (default .)
}).then(res  => {
	console.log('result->', res);
	/*
	{ 
		status: true,
		data:{ 
			format: 'jpeg',
			width: 256,
			height: 256,
			channels: 3,
			premultiplied: false,
			size: 9575,
			name: 'Q2m4yrR9Is.jpeg' 
		}
	}
	*/
}).catch(err  => {
	console.log('error->', err);
});

```
### Method cron({options})

```javascript

dnte.on('created', (info) => {
	console.log('file created->', info);
	/*
	{ 
		status: true,
		data:{ 
			format: 'jpeg',
			width: 256,
			height: 256,
			channels: 3,
			premultiplied: false,
			size: 9575,
			name: 'Q2m4yrR9Is.jpeg' 
		}
	}
	*/
}).cron({
	time: '*/10 * * * * *', // Generates an image every 10 seconds, and triggers the "created" event
	width: 256, // width of the image (default 128)
	height: 256, // high of the image (default 128)
	type: 'file',  // Type of file to generate (file or base64) (default file)
	path: 'avatars' // Path to save (Applies to type file) (default .)
});

```

## Results

![Imgur](https://i.imgur.com/9BZcepd.jpg)
![Imgur](https://i.imgur.com/6Mik0NN.jpg)
![Imgur](https://i.imgur.com/c4sMVAI.jpg)
![Imgur](https://i.imgur.com/2iP68s6.jpg)
![Imgur](https://i.imgur.com/qB1wmax.jpg)
![Imgur](https://i.imgur.com/jGcYhIA.jpg)


## Development

### Start

`npm start`

### Compile

`npm run compile`

### Watch

`npm run watch`

### Test

`npm test`

### Docs

`npm run docs`

## License

MIT © [Leonardo Rico](https://github.com/kevoj/thispersondoesnotexist-js/blob/master/LICENSE)
