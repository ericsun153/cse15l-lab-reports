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

* In this situation, we generate a new public key for the Github by using the code of `ssh-keygen -t rsa -C "git@github.com"`:

![Image7](Week6/2.3.jpg)

* After this, we should `cat` all the content of **id_rsa.pub** in the **.ssh** folder, and copy that into the *SSH key* in the account setting of Github.

![Image7](Week6/2.4.jpg)
![Image7](Week6/2.5.jpg)

* Then we use the link for the Github SSH key clone, which is `git@github.com:ericsun153/markdown-parser.git` for my *markdown-parser*, to clone our repository onto the *ieng6* server.

![Image7](Week6/2.6.jpg)

## Copy whole directories with `scp -r`
* First of all, we copy our entire **markdown-parse** directory to the *ieng6* server by using:
```
scp -r . cs15lsp22ang@ieng6.ucsd.edu:~/markdown-parse
```
* After we run `ls` in the command line, we can see the whole folder of **markdown-parse** has been copied to the server.

![Image8](Week6/3.1.jpg)

* Now we run JUnit test directly on the server, and we are able to find the following result by using the code:
```
cd markdown-parse; javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java; java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest
```

![Image9](Week6/3.2.png)

* Finally, in order to have a higher efficiency, we can use `scp`, `;`, and `ssh` to copy the whole directory and run the tests in one line.

```
ssh ieng6 "scp-r . cs15lsp22ang@ieng6.ucsd.edu:~/markdown-parse; cd markdown-parse; javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java; java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest"
```

* Therefore, after running this single line of command in the terminal, we can get the same result as the above.

![Image10](Week6/3.3.jpg)
![Image11](Week6/3.4.jpg)
