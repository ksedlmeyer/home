---
layout: post
title: Blocitoff
thumbnail-path: "img/CurrentTask.png"
short-description: Build a self-destructing to-do list application.

---

{:.center}
![]({{ site.baseurl }}/img/CurrentTask.png)

## Explanation

Everyone makes to-do lists, it is the easiest way to keep track of what items need to be done. The purpose of Blocitoff was to come up with a simple and easy to use to-do list that would keep itself from getting overrun with old tasks. Blocitoff is designed to delete tasks that are not completed after 7 days, the theory here being that if it hasn't been finished in that time, it is no longer important enough to be on the list.

## Problem

I was brought on to build the application from start to finish. There were 6 user stories that needed to be fulfilled by the application:

1. I want my tasks synced with a persistent backend
2. I want to see my active tasks in a list as my default view
3. I want completed tasks and tasks older than 7 days hidden from my main tasks automatically
4. I want expired and completed tasks presented in a separate view
5. I want to submit new tasks with a description, priority level and state of active
6. I want to mark tasks as complete 

## Solution

Through the use of Firebase, I was able to easily synch all data in the to-do list to a persistent backend. It kept track of all tasks that had been added, deleted and expired.

My landing page acted as the page where main and active tasks were added and viewed. I added a simple system for adding tasks that allows the user to add a description as well as assign a priority to the task. I set all tasks to automatically be active when first added.

In order for the system to recognize when a task was expired, I passed all tasks through a test to see how old they were. Once a task reached 7 days old, its state was changed from active to expired and then removed from the main task view using an ngHide method. I then created a second page to house all expired and completed tasks. Using ngShow, I enabled the viewer to see all of these expired and completed tasks on the separate page. I also chose to allow users the opportunity to keep their past tasks page organized by enabling the user to delete old tasks off the list as well. Any time they no longer wanted to see a task on any list, they could simply hit the delete button and it would be removed from the application all together. 

The final user story required that the user could simply click on a button to complete a task. I chose to create a method that, when clicked, would change the state of a task from active to expired and place it on the past tasks page allowing the user to view that task as completed.

## Results

I was able to test the code as I went along by deploying the application locally through grunt. This allowed me to use and view the app without having to make it viewable to the public. Most of the tests were easy to run simply through using the application.

I added tasks of my own as various times to ensure it was possible to place new tasks on the to-do list. In order to test the expiration of old tasks, I started by shortening the length of time that was checked for. I set the timer to expire tasks after only 10 seconds so that I could see if the application was properly moving tasks from the completed to expired task lists. Once I was sure it was working, I changed the length of time to the desired 7 days.

Because I was building this application on my own, I enlisted the help of a friend to test the ease of use of the application. She was able to easily navigate between the two lists, add tasks, and mark them as completed. When she first used the application, she made a comment about the past task list being incredibly long and unorganized. This is what actually led to my decision to enable users to delete past tasks from the list. It made for a more versatile use of the application.

## Conclusion

This was the first project I built on my own. I learned a lot about using angularJS to build an application. It is very interesting transitioning from doing tutorial projects to building an application from scratch.

If I were to do the project again, I would probably invest in the design elements of the application a bit more. It is an incredibly simple looking application and could benefit from some more styling.

Designing projects in the angularJS style appeals to me very much. I like how simple the code is when written. Being able to keep the html file so clean and using methods that repeat information are easy and clean ways to write and implement code. This is something I think will be very handy in the future.

A live version of this project can be found <a href=katies-task-list.herokuapp.com>here</a>.
