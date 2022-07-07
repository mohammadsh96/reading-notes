# GitTop group 



- ##  SooqCom :

It is a website that allows users to market real estate such as houses, apartments and lands. This website contains user real estate ads created within the website  

### as a visitor :

1- when i open the website it will show me a puplic route which is home page ("http://home") 

2-  in the home page  : 

   a- i will have   a form  that will ask me `optionally` to sign up /sign in 

   b- i will be able to see all `categories` within the website 
   
   
 3- if i click on any `category `.

   a- i will be able to `read all Users Posts` 

   b- when i try to  `interact` with any post it wont allow me and it will show me an alert ` "you should sign in  first .." ` 

4- i will be able to see other thing but keep it to the` front-end`


###  to become a user  :



1- to sign up in the website it will ask me to enter
   a-UserName 
   b-password
   c-phoneNumber
   d- email `"optional"` (maybe in the front-end)
   
   after `Submit` it will (generate a token for me and store in data base)  redirect me to sign in / login page or form in the same page (front-end)

2- to `sign in / login`  it will ask me to enter the `username `and `password` (bearer auth)  
    
    after submit it will redirect me to home page 


### as a User  :
1- i will be able to `read ` all post  (as usual) 
2- i will be able to  `create`  and `update` and `delete` my posts
3-i will be able to interact with other User posts (like , share , show phoneNumber , comment  and  `Chatting` with users)


### to post sothing (create)  : 

1- i will  click on a button (in the home page ) that will redirect me to another page (http://posts/create)
2- then i will have a form to create my post that ask me to enter :
   a-choose the department (sale estate , rent estate)
(**** it should have another category inside them  "think how to do it")

   b-  `enter a postname` 
   c- `enter a description` 
   d- `images `
   e-`Submit`

   after submit i will redirect me to ( http://posts/show)

### in Show page :

1- when i hit the route `/posts/show`, i will have two buttons :
    a-filteration  and Search
      b- first button will show me my posts , where i can (`read` ,`update`,`delete`)
      b- second  button will show me All users posts , where i can (`read` )
     

** if i click on first button  it will filter all posts and just show my posts by `Phonenumber`  and the `system will not accept same number` with different username **


----------------------------------------------
  GitTop group © nothing reserved ༼ つ ◕_◕ ༽つ  ||   to be continue ...
------------------------------------------------
<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

`not updated yet` 

⏳⏳⏳⏳⏳⏳⏳⏳⏳⏳
-----------------------
-  Features:

the Website has :

1- `Socket.io server` || REST API with socket.io packages

2-Users `Authentication` Using `bcrypt/Token`  for Sign in / sign up (basic and bearer authentication)

3-`database` / `model` for each category using `sequelize  `

4- categories made by `web socket rooms` as puplic rooms  

5-Enter and Leave categories Using `Events`

6-private rooms so regular User can send private messages to service provider  

7- sending notifications for Users


 the `service provider ` will be able to :

1-`create` new posts and `store` them to `database`

2-Do Full `CRUD` as an admin to his posts

3-receives notifications for interactions on his Posts


the regular user (The services seeker) will be able to :

1-`READ` and `interact` with other users posts 
2-different type of `filterations` like `city` , `price` ,`rating` ,(etc...)
3-send private maasages for  services provider 


----------

### for final project : 


with the front-end:

the user will be able to make real `Purchase order` and do `payments` for the products or services 

sending real `Emails ` and `phone calls` and `locations`


-------------
