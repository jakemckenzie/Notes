# Team Vulcan Minutes Week 7

## Minutes

For week 7 we met and talked about everyone's parts and who will need to doing 
handoffs together mostly on top of what their roles are. 

* Ammon is having difficulties running the camera SDK in python. The packaging has not 
been ported to pip yet so he'll either have to install it without pip which will be challenging 
or we will have to write all the image capturing in C++ which is fine because a lot of the example code 
is in C++ but that involves running a C++ file from python which we need to learn. Ammon is also 
making sure each part integrates properly and has taken on the systems engineering role from Jake.
* Alex Marlow is trying to optimize the object detection on the raspberry pi. Since the integration went seamlessly 
for his part into the raspberry pi now there are serious optimizations to be done to make it faster. This is going to 
be our most major bottleneck on processing and we're hoping that we can reduce the processing somehow on the pi and that 
our decision to not send anything over a network was a good choice.
* Jake needs to convert a bouncing box to a binary image. Complete the perspective transformation of the image. Currently we're 
planning on only doing that perspective transformation on the rectangle of the pickup area that the hemisphere exists within but 
that may change. The perspective transformation will not be needed for turning the robot. Once the binary image is working jake will 
start working on the orientationCapture algorithm which will sub up the rows and columns of each corer of the image. Since our bounding boxes 
are fairly tight we can split the image into 9 boxes and sum up the 8 boxes separately. The boxes with the greatest sum, say the box in the top 
left corner and bottom right will need hand orientation of 135 degrees.
* Brooke is figuring out the goto position for the hand and making one large function that will integrate with Alex's main arduino sketch.
Once this is done the orientation of the hand will be tested with Jake.
* Alex Boyle has been integrating all his separate arduino sketches together. That is mostly done and now he is moving onto avoiding obstacles and 
serial communication with the pi. Ammon created a constants file with various serial commands as bytes and we plan to communicate those back and fourth 
to each device. 

## Handshakes 
Alex Marlow -->  Ammon Dodson

(Alex integrated the object detection on the pi seamlessly but there are still 
issues. Object recognition with YOLO's running at 3 seconds on the pi but there are optimizations and handshakes the 
that need to happen in how the bounding box is integrated and how the code will be structure to 
deal with it. The github repository is fully integrated and the master branch is working on the pi though.)

Ammon Dodson <--> Alex Boyle

(Ammon and Alex will be dealing with the sending and receiving with the pi and arduino. We are saving our movements as 
we go so we will have to be logging our movements then dealing with sending and receiving coordinates captured on the pi 
then sending data calculated on the arduino back to the pi.)

Jake McKenzie --> Brooke Stevenson

(Jake needs to calculate the orientation and r and theta values for arm pivoting for brooke who is working on fine tuning 
the arm movements.)

Alex Marlow --> Jake McKenzie

(Alex needs to created bounding boxes on some syringes in the pickup area for Jake so that he can run binary image on it and do orientationCapture)

Brooke Stevenson <--> Alex Boyle

(Brooke and Alex need to make sure their parts compile and work properly together on the arduino)

Jake McKenzie --> Ammon Dodson

(Jake and Ammon need to make sure their parts on the raspberry pi compile and work properly together on the arduino)