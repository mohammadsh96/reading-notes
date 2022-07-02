# GitTop group / projects Ideas



- ## 1-  " e-commerce / open-sooq " :
it's a public store  which allows every one to sign up and offers his/her products or services and buy others products and services , or it can be personal website for  a company which provides specific types of services and products to customers and so the User will not post any thing in the website 



-  Features:

the Website has :

1- `Socket.io server` || REST API with socket.io packages

2-Users `Authentication` Using `bcrypt/Token`  for Sign in / sign up (basic and bearer authentication)

3-`database` / `model` for each category using `sequelize `

4- categories made by `web socket rooms` as puplic rooms  

5-Enter and Leave categories Using `Events`

6-private rooms so Users can send private messages to each others  

7- sending notifications for Users 


 the user will be able to :

1-`create` new posts and `store` them to `database`

2-Do Full `CRUD` as a user to his posts

3-`READ` and `interact` with other users posts : add to favorites / comments /likes /share / add to cart

4-recives notifications for interactions on his Posts

----------

### for final project : 


with the front-end:

the user will be able to make real `Purchase order` and do `payments` for the products or services 

sending real `Emails ` and `phone calls` and `locations`


-------------
--------
- ## 2  " library / E-Books " :
description: 

website for free right books with different types and categories 

(Fantasy ,Adventure,Romance,Contemporary,Dystopian,Mystery,Horror,Thriller,Paranormal,Historical fiction,Science Fiction,Children’s ,Memoir,Cooking,Art,Self-help / Personal,Development,Motivational,Health,History,Travel,Guide / How-to,Families & Relationships, Humo)

allowes users to read online free books Using free books API , or from fixed database as josn files contains books informations and content (if we can do that)  and maybe can download books as PDF files !! 

-  Features:

the Website has :

1- `Socket.io server` || REST API with socket.io package

2-Users `Authentication` Using `bcrypt/Token`  for Sign in / sign up (basic and bearer authentication)
(user, writer , editor , admin)

3-`database` / `model` for each category using `sequelize `

4- categories made by `web socket rooms` as puplic rooms  

5-Enter and Leave categories Using `Events`

6- sending notifications for Users 


 the user will be able to :

1-`READ` and `interact` : add to favorites / comments /likes /share 


----------

### for final project : 


with the front-end:

the user will be able to make move between categories and Read real books and make real `Purchase order` and do `payments` for the products or services 

sending real `Emails ` and `phone calls` and `locations`

--------
----

## 3- school website
It’s a web page of school or university. 
Users can sign up and sign in. We can make signing up process done by username, password and a code given to users, let’s say as a range between numbers to be accepted to sign up. This for Auth. and we can use sequelize to store users (students, instructors and ITs). We can make special code for students in a range and instructors in another different range so that no students sign up as instructors and we can use these codes later on in rooms and communication. For sure, these codes must be unique as username in users sequelize. 
Communication process by Socket.io, we can make private rooms between any users and room for inst. and ITs, and special room for students. As a university we can make things more particular because of differentiation between departments, you know each department has inst. and students.
For final project we can design everything and link it to our backend project and through working on the project we might find some enhancements to be done.