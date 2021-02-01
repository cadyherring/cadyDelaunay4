# cadyDelaunay4
inProgress

#made using openFrameworks of_v20210131_osx_release 
find here: https://openframeworks.cc/download/
under nightly builds

Delaunay video
In this assignment you'll have to study the code provided and do something interesting with the data extracted by the algorithm. The idea is to built something similar to what Memo did for the video below:
http://www.memo.tv/portfolio/wombats-techno-fan/
Read the documentation he wrote about it here (click on "more" on the right).


General instructions
Generate a new project and include the ofxOpenCV and ofxDelaunay addon (link to the latter)
https://github.com/obviousjim/ofxDelaunay
Copy the code from the goodFeaturesToTrack example
When you run the code you'll see some red points. These are corners in the image and are considered "good points to track" as used by the inner function of openCV (not ofxCV). See the documentation page of the algorithm for what the parameters mean.
Open the Flatlander assignment from week 11 and copy the code from ofApp.h the declaration of the ofxDelaunay object (called triangulation).
The goodFeaturesToTrack() function puts all the good features inside the corners vector. Under the goodFeaturesToTrack() call, reset the triangulation object and loop over the corners vector adding each corner to the triangulation. Inside the aforementioned loop you'll have something like this:

triangulation.addPoint(ofPoint(corners[i].x, corners[i].y));
You need this ofPoint() conversion because corners is of type Point2f.

After the loop, call the triangulate() command on the object and we'll be ready to plot the results.
Go back to the Flatlander code and copy the getTriangle() function I provided. Make sure you also copy the declaration from the ofApp.h file.
Go back to the Flatlander example and copy the bit that loops over all of the triangles and draws them. Copy that for loop inside the draw() function of your new code.
Outside the loop make a call to ofNoFill();. If you've done everything right it should draw a delaunay diagram based on the points it thought were important. Let's put some color to it.
Remove the ofNoFill() call.
Inside the same loop you'll notice that we're storing the points of each triangle inside a vector called pts. This vector has 3 points. Calculate the average coordinate of these 3 points (ie, the center of the triangle). We're going to use this coordinate to decide what color to give to the triangle.
Say you stored the center of the triangle in two variables x and y make this call to get the color under that pixel: image.getPixels().getColor(x,y)); Store the returning value to an ofColor object and make a call to ofSetColor() before you make a call to ofDrawTriangle() in the line below. If you've done everything right you should be seeing what the video below shows. 
