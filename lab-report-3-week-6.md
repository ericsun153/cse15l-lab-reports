# How can we access our Github on the server of `ieng6`?
## Streamlining ssh Configuration
* First of all, we should find the **.ssh** folder on our local computer. (Mine is in the local user profile)

![Image1](Week6/1.1.jpg)

* After we going into the folder, we can already see the file called **id_rsa.pub** that we used it to store our passward on this local computer so that we can login the server without typing the passward.

* So now we want to make the login process even more quicker. Firstly we create a **txt** file called **config.txt**, and I put the following text into it:
```
Host ieng6
    HostName ieng6.ucsd.edu
    User cs15lsp22ang (This is my username)
```
* Then we save the file and delete the extension of **txt**. 

![Image2](Week6/1.2.jpg)

![Image3](Week6/1.4.jpg)

* At last we open the Terminal and directly type `ssh ieng6`, and we can see that new login is faster and easier to type!

![Image4](Week6/1.3.jpg)

* What if we want to copy a file from local computer to the server? We use the command of `scp`. Firstly we copy the file onto the server:

![Image](Week6/1.3.1.jpg)

* After that, we log back onto the server and we are able to see that the **HelloWorld.txt** has been successfuly copied to *ieng6*.

![Image](Week6/1.3.2.jpg)

## Setup Github Access from ieng6
* For this step, we firstly clone our repositary of **markdown-parser** onto the *ieng6* server.

![Image5](Week6/2.1.jpg)

* Now after making some changes to the **MarkdownParse.java**, when we `push` the file back to the Github, we can find that it appears an error for that we cannot use the password authentication to access Github.

![Image6](Week6/2.2.jpg)

* In this situation, we generate a new public key for the Github:

![Image7](Week6/2.3.jpg)

## Copy whole directories with `scp -r`
* 
