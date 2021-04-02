# CollegeChat

## Table of Contents
1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)
2. [Schema](#Schema)

## Overview
### Description
CollegeChat is a social networking application for college students and instructors. Each college will have all offered classes listed on the main page. Students will have access to their designated classes. College admin has the power to monitor all the group chats and posts. Students can have smoother communication with their instructors. Since everything is in distance learning, this application will increase the collaboration between students and instructors.

### App Evaluation
- **Category:** Social Networking
- **Mobile:** Initially, this application is designed for the mobile platform. Later on, there is a plan to develop this for web applications with the same functionality.
- **Story:** Students and instructors will have easy access to communicate with each other and post study-related materials for each class.
- **Market:** Each College will have an admin who will give access to students and instructors to use the application.
- **Habit:** This application is very user-friendly to students and instructors. They can use this application during the whole semester time.
- **Scope:** Students can get a quick reply from their instructors because, through this application, it will not take a long time for instructors to give responses to any students.

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**

* Common User Stories:
  * [ ] Login/LogoutCancel changes
  * [ ] chats
  * [ ] Notifications
* Admin User Stories:
  * [ ] Add and edit colleges 
* College User Stories:
  * [ ] Create individual rooms for each class/club/organization 
  * [ ] Name rooms
  * [ ] Reset rooms 
  * [ ] Assign professor/group admin to classes via code/email
* Instructor User Story:
  * [ ] Invite students by class code/email (with college + class identifier) 
  * [ ] Remove students
  * [ ] Post on bulletin board
  * [ ] Delete posts of self and other students
  * [ ] Chat messages to students 
  * [ ] Delete chats messages of other students
* Student User Story:
  * [ ] Create account
  * [ ] Reply to posts
  * [ ] Send direct messages other students
  * [ ] Send messages in group chat


**Optional Nice-to-have Stories**

* Partially reset room
* Group sections under a single class e.g. 5 different sections under Math 161A
* Customize group chats
* Reset codes
* Instructor can delete own messages 
* Onboarding


### 2. Screen Archetypes
 
* Login/Register
  * College Admin Home
  * Student Home
  * Instructor Home
  * App Admin Home

* Stream
  * Respective user can view all college chats/classes
  * App Admin Home, provide UI for admin actions

* Creation
  * College user can add classes
  * Add app admin
  * Student add class
  * Student new post
  * Instructor new post

* Profile
  * User can view profile

* Settings
  * Instructor user can view settings of chat
  * College user can edit class settings
  * College user can edit college settings
  * Edit app admin
  * Edit user

* Messaging
  * Respective User messaging


### 3. Navigation

**Tab Navigation** (Tab to Screen)

* Add Class
* Add College
* Add College Administrator
* Add App Admin
* New Message
* New Post
* Chats
* Logout
* Settings


**Flow Navigation** (Screen to Screen)

* [list first screen here]
   * [list screen navigation here]
   * ...
* [list second screen here]
   * [list screen navigation here]
   * ...

* SignUp
  * Login screen

* Login Screen
  * College Admin Home
  * Student Home
  * Instructor Home
  * App Admin Home

* College Admin Home
  * Edit Class

* Student Home
  * Student Posts
  * Student Profile
  * Student Add Class

* Instructor Home
  * Instructor Add class
  * Instructor Profile
  * Teacher Posts

* App Admin Home
  * Add College
  * Colleges
  * App Admins
  * Users


## Wireframes
Home Screens
<img src="https://drive.google.com/file/d/1mYDmj0Cbuo8EOKrbYxdC7i8QyU52ZcHX/view?usp=sharing" width=600>
App Admin
<img src="https://drive.google.com/file/d/1mnIgnn0orBdvn6W6pFdMWw2V9ruFQDsi/view?usp=sharing" width=600>
College Admin
<img src="https://drive.google.com/file/d/1_Ma36ZQYb-KMB7gSjK2jOdPJztSI7hk6/view?usp=sharing" width=600>
Instructor
<img src="https://drive.google.com/file/d/1mtINe85cn4zjp1NNax0lSt9vRuJIXOMa/view?usp=sharing" width=600>
Student
<img src="https://drive.google.com/file/d/1ESvpa_p2htO1EIAOCAoQHqEoV_x46UAn/view?usp=sharing" width=600>

### [BONUS] Digital Wireframes & Mockups

### [BONUS] Interactive Prototype
https://xd.adobe.com/view/8d4918dc-65f3-44cb-819c-48a28f72e2a7-d81a/

## Schema 
[This section will be completed in Unit 9]
### Models
[Add table of models]
### Networking
- [Add list of network requests by screen ]
- [Create basic snippets for each Parse network request]
- [OPTIONAL: List endpoints if using existing API such as Yelp]
