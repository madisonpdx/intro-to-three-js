WebGL
-----

WebGL is a technology available in newer web browsers that allows you to display 3D content such as animations and games. In the past, to write a 3D game you would have had to use complex desktop applications, but now we can make a 3D game using nothing but a text editor and a web browser.

Three.js
--------

Three.js is a tool that builds on the WebGL technology and makes it easier create objects in 3D. There are some pretty amazing examples of things you can create on the Three.js website.

[Three.js Website](http://threejs.org/)

<<<<<<< HEAD
Chrome Security Issue
---------------------

Google Chrome will prevent our 3D games from running when the files are stored on our computer instead of on a web server. To get around this issue make sure Chrome is completely closed. Open a command prompt and enter the command:

```
open -a Google\ Chrome --args --disable-web-security
```

Getting Started
---------------

Download Sublime Text and this project. Copy the project to your desktop then open the project folder in Sublime Text.

Make The Background Look Like Space
-----------------------------------

Our background is currently white, which doesn't look like space. Let's make it black instead. Find this line of code and change from 0xffffff which is the hex value of white to 0x000000 the hex value of black.

```
renderer.setClearColor(0xffffff);
```

Make Earth Look Like Earth
--------------------------

Right now the Earth is just a blue sphere. There is an image in the img folder that we can wrap around the sphere so that the earth will have continents, oceans, and clouds.

```
earthMaterial = new THREE.MeshPhongMaterial({
    map: THREE.ImageUtils.loadTexture('img/earth.jpg'),
    transparent: false
});
```

The Earth is rotating, but it might be more interesting if it moved a little faster. Look in the animate function and change the line that sets the speed of Earth's rotation. 

```
earthMesh.rotation.y += 0.001
```

Add The Moon
------------

Copy the code that creates the Earth and in your copied code change all the words earth to moon.

'''
// create a sphere to represent the earth
moon = new THREE.SphereGeometry(100, 32, 32);
// create a texture to give the earth some color.
moonMaterial = new THREE.MeshBasicMaterial({
    color: 0x0000ff 
});
// create a 3D mesh using our earth sphere and it's texture.
moonMesh = new THREE.Mesh(moon, moonMaterial);
scene.add(moonMesh);
'''

You'll have to adjust some parameters to make the moon smaller than the earth and use the image for the moon instead of the Earth. Also, you need to change the position of the moon so you can see it. Right now it's at the center of the earth. Try something like:

```
moonMesh.position.y = 200;
```

Make The Moon Orbit
-------------------

Finally, add the following code to the animate function. As our animation runs this will cause the moon to be moved in an orbit around the earth.

```
var rotSpeed = -.02;
moonX = moonMesh.position.x;
moonY = moonMesh.position.y;
moonZ = moonMesh.position.z;
moonMesh.position.x = moonX * Math.cos(rotSpeed) - moonZ * Math.sin(rotSpeed);
moonMesh.position.z = moonZ * Math.cos(rotSpeed) + moonX * Math.sin(rotSpeed);
```
=======
Challenge
----------

Download this example and open it in your text editor (Sublime Text). This example shows a red sphere with a spotlight that lights it up. See if you can make it a blue sphere instead. Then change it to a cube instead of a sphere. Add an additonal light to the scene or try with a different type of light. 

You can use [Adobe Kuler](https://kuler.adobe.com/) to find the hex values of colors.
>>>>>>> 138f34b0cd63d1896e768d0be61aaf7d47e78bd1
