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

<img src="https://github.com/CollegeChat/CollegeChat/blob/main/Wireframes/Home.png" width=600>

App Admin

<img src="https://github.com/CollegeChat/CollegeChat/blob/main/Wireframes/App%20Admin.png" width=600>

College Admin

<img src="https://github.com/CollegeChat/CollegeChat/blob/main/Wireframes/College%20Admin.png" width=600>

Instructor

<img src="https://github.com/CollegeChat/CollegeChat/blob/main/Wireframes/Instructor.png" width=600>

Student

<img src="https://github.com/CollegeChat/CollegeChat/blob/main/Wireframes/Student.png" width=600>

### [BONUS] Digital Wireframes & Mockups

### [BONUS] Interactive Prototype
https://xd.adobe.com/view/8d4918dc-65f3-44cb-819c-48a28f72e2a7-d81a/

## Schema 
### Models
**Users**
| Property | Type |
| -------- | ---- |
| email | String |
| password | Char | 
| fistname | String |
| lastname | String |
| DOB | Date |
| profilePic | File |
| accountType | String |

**Colleges**
| Property | Type |
| -------- | ---- |
| name | String |
| email | String | 
| address | String |

**Chatrooms**
| Property | Type |
| -------- | ---- |
| inviteCode | Char |
| collegeName | String | 
| instructorEmail | String |
| chatName | String |
| description | String |
| chatPic | File |

**Registers**
| Property | Type |
| -------- | ---- |
| inviteCode | Char |
| studentEmail | String | 

**Posts**
| Property | Type |
| -------- | ---- |
| postID | Char |
| sender | String | 
| postFile | File |
| content | String |
| replyPostID | Char |
| timestamp | Datetime |

**Messages**
| Property | Type |
| -------- | ---- |
| messageID | Char |
| sender | String | 
| receiver | String |
| content | String |
| timestamp | Datetime |


### Networking
Homescreen
* Login (Get username data and compare credentials)
    
    ```swift
    let username = usernameTextField.text!
    let password = passwordTextField.text!
    PFUser.logInWithUsername(inBackground: username, password: password) { (user, error) in
        if user != nil{
            self.performSegue(withIdentifier: "loginSegue", sender: nil)
        } else {
            print("Error: \(error?.localizedDescription)")
        }
    } 
    ``` 
* Signup (Insert new user data in DB) 
       
    ```swift
    user.username = usernameTextField.text
    user.password = passwordTextField.text
    user.email = "email@example.com"
    user.signUpInBackground { (success, error) in
        if success {
            self.performSegue(withIdentifier: "loginSegue", sender: nil)
        } else {
            print("Error: \(error?.localizedDescription)")
        }
    }
    ```
College Admin
* College Admin Home (Display chatrooms/classes)
```swift
    var chatrooms = [PFObject]()
    let query = PFQuery(className: "Chatrooms")
    query.includeKeys(["chatName", "chatPic"])
    query.limit = 20
    query.findObjectsInBackground { (chatrooms, error) in
        if chatrooms != nil {
            self.chatrooms = chatrooms!
            self.tableView.reloadData()
        }
        else {
            print("Error: \(error)")
        }
    }
```
* Add class (Store class/chatroom data in DB)
```swift
    let chatroomTable = PFObject(className: "Chatrooms")
    let college_name = collegeNameTextField.text!
    let instructor_email = instructorEmailTextField.text!
    let chat_name = chatNameTextField.text!
    let description = descriptionTextField.text ?? ""

    let imageData = chatPicView.image!.pngData()  //default pic
    let file = PFFileObject(data: imageData!)
    let chat_pic = chatPic

    chatroomTable[“inviteCode”] = invite_code
    chatroomTable[“collegeName”] = college_name
    chatroomTable[“instructorEmail”] = instructor_email
    chatroomTable[“chatName”] = chat_name
    chatroomTable[“description”] = description
    chatroomTable[“chatPic”] = chat_pic
    
    chatroomTable.saveInBackground { (success, error) in
            if success {
                self.dismiss(animated: true, completion: nil)
                print("saved!")
            } else {
                print("error!")
            }
     }
```

* Edit class (Display existing class data from DB + Modify/save class/chatroom data in DB + Delete class)
 ```swift
    var chatrooms = [PFObject]()
    let query = PFQuery(className: "Chatrooms")
    query.includeKeys(["inviteCode", "collegeName","instructorEmail", "chatName",“description”, "chatPic"])
    query.limit = 20
    query.findObjectsInBackground { (chatrooms, error) in
        if chatrooms != nil {
            self.chatrooms = chatrooms!
            //set properties
        }
        else {
            print("Error: \(error)")
        }
    }
    
    let chatroomTable = PFObject(className: "Chatrooms")
    let college_name = collegeNameTextField.text!
    let instructor_email = instructorEmailTextField.text!
    let chat_name = chatNameTextField.text!
    let description = descriptionTextField.text ?? ""

    let imageData = chatPicView.image!.pngData()  //default pic
    let file = PFFileObject(data: imageData!)
    let chat_pic = chatPic

    chatroomTable[“inviteCode”] = invite_code
    chatroomTable[“collegeName”] = college_name
    chatroomTable[“instructorEmail”] = instructor_email
    chatroomTable[“chatName”] = chat_name
    chatroomTable[“description”] = description
    chatroomTable[“chatPic”] = chat_pic
    
    chatroomTable.saveInBackground { (success, error) in
            if success {
                self.dismiss(animated: true, completion: nil)
                print("saved!")
            } else {
                print("error!")
            }
     }
```
* College settings (Display/retrieve college data from DB + Modify college data in DB)
```swift
    var college = [PFObject]()
    let query = PFQuery(className: "Colleges")
    query.includeKeys(["name", "email", "address"])
    query.limit = 20
    query.findObjectsInBackground { (college, error) in
        if college != nil {
            self.college = college!
            //set properties
        }
        else {
            print("Error: \(error)")
        }
    }
    
    let collegeTable = PFObject(className: "Chatrooms")
    let college_name = collegeNameTextField.text!
    let college_email = collegeEmailTextField.text!
    let college_address = collegeAddressTextField.text!

    collegeTable[“name”] = college_name
    collegeTable[“email”] = college_email
    collegeTable[“address”] = college_address
    
    collegeTable.saveInBackground { (success, error) in
            if success {
                self.dismiss(animated: true, completion: nil)
                print("saved!")
            } else {
                print("error!")
            }
     }
```

App Admin
* App Admin Home (Retrieve data from DB)
* App Admins (Retrieve app admin data from DB)
* Add App Admin (Store data in DB)
* Edit App Admin (Retrieve app admin data + Modify/store app admin data + Delete app admin)
* Users (Retrieve users data from DB)
* Edit User (Retrieve users data + Modify/store app admin data + Delete user)

Student
* Student Home (Retrieve chatrooms from Registers table from DB)
* Student Add Class (Store data in Registers table)
* Student Profile (Display student data + Modify student data from DB)
* Student Posts (Retrieve chatroom posts and replies)
* Student New Post (Save data in DB)
* Student Post Info (Retrieve post info/replies from DB)
* Student Post Reply (Save reply/post info in DB)
* Student Group Chat (Retrieve messages + Save new messages)
* Student Chat Settings (Display chatroom info + remove student from Chatroom if leave)
* Student Messages (Display student DM messages info from DB)
* Student New Message (Query searched user)
* Student Direct Message (Retrieve messages + Save new messages)

Instructor 
* Instructor Home (Retrieve chatrooms from Registers table from DB)
* Instructor Add Class (Store data in Registers table)
* Instructor Profile (Display student data + modify student data from DB)
* Instructor Posts (Retrieve chatroom posts and replies + remove posts and replies)
* Instructor New Post (Save data in DB)
* Instructor Post Info (Retrieve post info/replies from DB + delete replies)
* Instructor Post Reply (Save reply/post info in DB)
* Instructor Group Chat (Retrieve messages + save new messages + delete messages)
* Instructor Chat Settings (Display chatroom info + remove student from Chatroom)
* Instructor Edit Group (Modify/Update chatroom info)
* Instructor Messages (Display student DM messages info from DB)
* Instructor New Message (Query searched user)
* Instructor Direct Message (Retrieve messages + Save new messages)


- [Add list of network requests by screen ]
- [Create basic snippets for each Parse network request]
- [OPTIONAL: List endpoints if using existing API such as Yelp]
