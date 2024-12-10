Html2img   maybe   nodejs canvas jsdom ok



const { Canvas, createCanvas, Image, ImageData, loadImage } = require('canvas');
const { JSDOM } = require('jsdom');
const { writeFileSync, existsSync, mkdirSync } = require("fs");




Emulating HTML DOM and canvas
As you might already seen, the rest of the examples use functions like cv.imread(), cv.imshow() to read and write images. Unfortunately as mentioned they won't work on Node.js since there is no HTML DOM.
In this section, you will learn how to use jsdom and node-canvas to emulate the HTML DOM on Node.js so those functions work.

