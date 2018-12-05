# Video Doorbell, Lab 7

*A lab report by John Q. Student*

### In This Report

1. Upload a video of your version of the camera lab to your lab Github repository
1. As usual, update your class Hub repository to add your [forked IDD-Fa18-Lab7](/FAR-Lab/IDD-Fa18-Lab7) repository.
1. Answer the questions in-line below on your README.md.

## Part A. HelloYou from the Raspberry Pi

**a. Link to a video of your HelloYou sketch running.**

[Hell You](https://drive.google.com/file/d/1KDEGXb8DVXPry_bzLI58nrgxbkR9y7XD/view?usp=sharing)

## Part B. Web Camera

**a. Compare `helloYou/server.js` and `IDD-Fa18-Lab7/pictureServer.js`. What elements had to be added or changed to enable the web camera? (Hint: It might be good to know that there is a UNIX command called `diff` that compares files.)**

I added the image capturing code:

```javascript
var imageName = new Date().toString().replace(/[&\/\\#,+()$~%.'":*?<>{}\s-]/g, '');
console.log('making a making a picture at' + imageName); // Second, the name is logged to the console.
//Third, the picture is  taken and saved to the `public/`` folder
NodeWebcam.capture('public/' + imageName, opts, function(err, data) {
    io.emit('newPicture', (imageName + '.jpg')); ///Lastly, the new name is send to the client web browser.
    /// The browser will take this new name and load the picture from the public folder.
});
```

to the function that is reading and parsing the serial data.  When `data == 'dark'`, execute the image capture code.

**b. Include a video of your working video doorbell**

[Door Bell](https://drive.google.com/file/d/1CqjeB_cVxZV8lG3HBw7oxIlrZ-AZyGKw/view?usp=sharing)

## Part C. Make it your own

**a. Find, install, and try out a node-based library and try to incorporate into your lab. Document your successes and failures (totally okay!) for your writeup. This will help others in class figure out cool new tools and capabilities.**

I wanted to convert the image into ascii art.  I found this really great node package called [`image-to-ascii`](https://www.npmjs.com/package/image-to-ascii).  I was able to easily covert the picture and print the ascii to the console.  When I tried to display the text in the webpage the text lost its formatting. 

**b. Upload a video of your working modified project**

[Image to Ascii](https://drive.google.com/file/d/1ekP_esuD6_Y11e2KITwPEcgU0iiLYRHc/view?usp=sharing)
