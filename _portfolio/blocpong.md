---
layout: post
title: Blocpong
thumbnail-path: "img/blocipedia.png"
short-description: Use pure Javascript and the HTML5 canvas element to create a Pong replica.

---

{:.center}
![]({{ site.baseurl }}/img/blocipedia.png)

## Explanation

The point of the project was to experience how fun it could be to build a project using only basic Javascript object orientation. It was very focused on controlling how objects moved and worked together to recreate a classic arcade game. As a developer it allowed me to expand my grasp of Javascript while also creating an application that was purely for enjoyment.

## Problem

I was provided with six user stories to fulfill in this project.

1. I want to see a Pong table, two paddles, and a ball.
2. I want to control the position of a paddle with arrow keys.
3. I want the ball to bounce off the paddles and two sides of the table.
4. I want to play against a computer opponent.
5. I want to see the score update live.
6. I want the game to end when a player scores 11 points.

## Solution

I created the table using the HTML5 canvas element. This was a simple way to create a table that I could then use as a coordinate plane and easily position my other objects accordingly. I used an object constructor to create the paddles. This method was chosen because it keeps my code as simple as possbile. Instead of creating two separate objects that would have the same properties, I was able to create one that would house all the basic information required to build a paddle. I built the ball using the same constructor method. Since the computer would have to regenerate the ball after each point was scored, this constructor was a single place for the application to grab the necessary information. I used the render method on each of my constructor's to display the objects on my canvas. I set the objects to render on window.onload so that they would appear as soon as the player opened the screen.

In order to make the game ready for animation I had to create a function that would call requestAnimationFrame. Mine was set to call a callback 60 times persecond and continuously reanimate the game.

{% highlight javascript %}
var animate = window.requestAnimationFrame ||
        window.webkitRequestAnimationFrame ||
        window.mozRequestAnimationFrame    ||
        window.oRequestAnimationFrame      || 
        window.msRequestAnimationFrame     ||
        function(callback) { window.setTimeout(callback, 1000/60) };
{% endhighlight %}

After setting this up I had to add a speed and direction to the movement of my paddles. I added a property that specified how many pixels they would move per key press. After this, I called .addEventListener() on the object to listen for the player's key presses. The player paddle was then set to move according to when the player struck the left and right arrow keys.

I tackled the animation of the ball next. The movement of the ball was a little bit more tricky because it moves across both the x and y axis. The important thing to remember was that the center of the ball was the position that was being tracked. That meant that all collisions had to be detected 5 pixels from the ball's tracked position because it had a radius of 5 pixels. I set it to detect when the outer edge of the ball is equal to the table side and top coordinates as well as the coordinates of the paddle. Anytime it collided with something it would bounce off at a predetermined speed in a new direction.

The most challenging part was animating the computer. I had to se the computer paddle to adjust it's position based on where the ball was located on the coordinate plane. My AI was very simple. It had a max speed that it would reach in order to give the player a chance to score points. Using an update method on the computer paddle constructor I created a function that moved the paddle to match the position of the ball on the axis. It was no complex at all which allowed me to create a simple game that could be made more complex at a later time.

In order to track and display the score live, I created two variables to hold the scores. They were set to start at 0 and increase by one each time a point was scored. To display the score, I created HTML elements to house the scores. DOM selectors selected the elements that were then grabbed using the innerHTML property to assign the players' scrores to the designated HTML elements. Very simple.

The final piece to the puzzle was setting the game to terminate after a player reached 11 points. I achieved this by simply checking the players' scores after each point to see if it equaled 11. Once a player did reach 11, a message was displayed on the screen. Is the player reached 11 points, the game would display a "You won!" message. If the computer reached 11 points, the game would display a "You lost!" message. At this point the game would also display a message telling the player to refresh the screen to play again.

## Results

It was easy to test my code throughout this project. I would simply load the page housing the game and see if everything was working properly. The most important aspect to me during the whole testing process was ensuring that the game actually looked like the classic version of pong. I did this by setting my css to display everything in black and white and use chunkier test that would look somewhat pixelated as it would if it were being displayed on an arcade screen. The whole process started with a lot of trial and error as I started to figure out how to implement the proper use of object oriented Javascript.

## Conclusion

This is obviously a very unique use of Javascript. While I don't see myself building arcade games for the rest of my career, I think it very useful to fully explore the different uses of a language. I saw the versatility of Javascript as an application builder. 

It also helped strengthen the confidence I had in myself. I was able to really dive into this project and tackle the difficulties of creating a AI system that would respond to live changed in an application. I finished the project feeling like I had a better grasp on Javascript as a language and with a better ability to utilize it in the future.