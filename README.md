# Notes and Important Formulas
##### From *Billy Lamberta's* **FOUNDATION HTML5**


### Converting between Radians and Degrees
	
	DEGREES TO RADIANS 
		radians = degrees * Math.PI / 180

	RADIANS TO DEGREES
		degrees = radians * 180 / Math.PI


### Acceleration and Velocity Manipulation

	CONVERT ANGULAR VELOCITY TO X,Y VELOCITY
		vx = speed * Math.cos(angle); // In Radians
		vy = speed * Math.sin(angle); // In Radians

	CONVERT ANGULAR ACCELERATION TO X,Y ACCELERATION
		ax = force * Math.cos(angle);
		ay = force * math.sin(angle);

	ADD ACCELERATION TO VELOCITY
		vx += ax;
		vy += ay;

	ADD VELOCITY TO POSITION
		object.x += vx;
		object.y += vy;


### Dealing with Objects Going Off Screen

	REMOVE AN OUT-OF-BOUNDS OBJECT
		if (object.x - object.width / 2 > right ||
			object.x - object.width / 2 < left ||
			object.y - object.height / 2 > bottom ||
			object.y + object.height / 2 < top) {
				// reset object position and velocity.
			}


## Chapter 5
Velocity: speed in a particular direction. <br>
Vector: Something that has magnitude (speed) and direction.<br>
<br>
Although there is no such thing as negative magnitude, magnitude in the opposite direction can be described (in our case) as negative magnitude. <br>
We can calculate an objects position by adding velocity to it's current position (object.x += vx).<br>
The sum of 2 vectors can be thought of as angular velocity.Angular velocity combines the velocity of more than one axis (x and y, in our case). 

## Chapter 6
Inertia: the tendency of an opbect in motion to *stay* in motion.<br>
Boundaries: an enclosed space for the 'action' to take place. When an object crosses the boundries, we can take the following actions:<br>
  1. Remove it.<br>
  2. Regeneration.<br>
  3. Wrap it on the screen (if it leaves the left side bring it back on the right).<br>
  4. Bounce it against the boundry.<br>

#### Removing Objects
When working with multiple objects it can be helpful to store them in an array. Then, once they leave the screen, we can use *array.splice* to remove them. <br>
When deciding to remove an object, it is a good idea to take the width of the object into account. If the position of the object is measured by the center of the object, we want to add half the width in this calculation. This ensures we don't see the remaining half *disappear* off the screen.
#### Screen-Wrapping
For screen-wrapping, we chage the position of the object once it goes off the screen. We let the object move *completely* off the canvas before we reposition. 
#### Bouncing
To bounce an object we want to reverse it's velocity: If it bounces on the top or bottom, reverse the Y velocity. If it bounces on the left or right, bounce the X velocity. To reverse the velocity, just multiply by -1.
We want to take care that the object we're bouncing does not leave the screen - not even a little bit. This will give an unrealistic effect, we want to avoid this!
When we reverse the velocity, we want to ensure that the position of the ball is directly against the edge of the canvas. If we don't do this, the object can get stuck within the boundry of the canvas - stuck in an endless loop of velocity reversal. In our if statement we will position the object exactly to where our statement is checking for it. 
Steps:	1. Check if it went past the boundry.
		2. Reposition the object on the edge.
		3. Reverse velocity.
#### Friction
Also known as friction, drag, resistance, damping. Friction affects the magnitude of velocity, but not the force. 

## Chapter 8
Easing - Proportational Motion.<br>
Springing - Proportional Acceleration.<br>
#### Proportional Motion
  1. Set a target.
  2. Determine the distance to target.
  3. Make motion proportional to distance.

If we are always moving a proportional distance to our target, will we ever get there? If each time we move half the distance to the target, we could be doing this till infinity. **BUT** we will get to a point that is *close enough*. We need to figure out what this point is, so we can stop computations and 'arrive' at our target. 

Note: Easing can be used for properties other than position (color, rotation, transparency).

	EASE ROTATION
		var rotation = 90,
			targetRotation = 270;
		rotation += (targetRotation - rotation) * easing;
		object.rotation = rotation * Math.Pi / 180; // convert degrees to radians



	EASE COLORS 
	// here we go from red to blue
		var red = 255,
			green = 0,
			blue = 0,
			redTarget = 0,
			greenTarget = 0,
			blueTarget = 255;

	// in draw function
		red += (redTarget - red) * easing;
		green += (greenTarget - green) * easing;
		blue += (blueTarget - blue) * easing;

	// combine components
		var color = red >> 16 | green << 8 | blue;










