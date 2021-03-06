# raspberrypi_node_camera_web_streamer
<h3>Stream a realtime raspberry pi camera feed through an HTML web page</h3>

After many hours of searching the web, I realized that, as prolific as raspberry pi's, cameras, and node.js are, there was no fusion of the three. I wrote this node.js solution in response to that in hopes that others may find it useful. This project can serve as a stand-alone video streamer or as a template for a much more complicated project.

The camera is streamed as a .mjpeg file into a &lt;img /&gt; tag. The implementation is simple yet fully effective.

<h3>Install via npm</h3>
To just use the streamer without the example content, you can install via npm:
<code>npm install raspberrypi-node-camera-web-streamer</code>

Then in your js, you can start it like this:
<pre>
const app = express(); 
const videoStream = require('raspberrypi-node-camera-web-streamer');
videoStream.acceptConnections(app, {
    width: 1280,
    height: 720,
    fps: 16,
    encoding: 'JPEG',
    quality: 7 //lower is faster
}, '/stream.mjpg', true);
</pre>

<code>videoStream.acceptConnections</code> accepts 4 parameters: <code>express</code> module, <code>settings object</code> (optional), <code>path</code> to host the streaming resource (optional), and <code>isVerbose</code> (optional).

<b>NOTICE: </b>Express for Node.js is required. If you don't want to use Express, it's not hard to fork the repo and modify it.


<h3>Install via git</h3>

Assuming you already have node.js installed, steps to install are:

1) Download the repo

2) Restore dependencies by running <code>npm install</code> from within the folder of the repository

3) Start the server by running <code>node index.js</code>

4) Navigate to the new site by going to <code>http://<ip_address>:3000</code>

Anything inside the <code>public</code> folder is hosted as static content. The index.html page gives an example of how to stream from the camera. Streaming quality settings can be modified within the index.js file.


