# Notes and Important Formulas
##### From *Billy Lamberta's* **FOUNDATION HTML5**


### Converting between Radians and Degrees
	
	DEGREES TO RADIANS 
		radians = degrees * Math.PI / 180

	RADIANS TO DEGREES
		degrees = radians * 180 / Math.PI


	-- Chapter.5 --

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
