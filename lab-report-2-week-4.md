# How to find a *failure-inducing input*, and use it to test and debug our code efficiently?
## Setups
> In this lab report, we will mainly focus on incremental and test-driven development that can let us test and debug our program more easily, logically and effieciently.


* The first step is to use the **Fork** function of Github, it can makes a copy of the repository on your own Github page.


![Image1](Week4/Fork.jpg)

* Then we **Fetch** this repository to our Github desktop in order to implement the debug process on our own Visual Studio Code:

![Image2](Week4/Fetch.jpg)
```
javac MarkdownParse.java
java MarkdownParse test-file.md
```

## Breaking Tests
> The following are different **breaking tests** under different situations that I found during the testing and debugging process of `MarkdownParse.java`.

### Test 1：Infinite loop
> The first breaking test case is happening when I add one extra blank line at the end of the test-file markdown.
![image3.5](Week4/Test1case.png)


* Code changes:

![image3](Week4/Test1code.png)

* [Here](https://github.com/ericsun153/markdown-parser/blob/main/test-file.md) is the link to my breaking test case 1 of **Infinite Loop**.

* Symptom:

![image4](Week4/Test1symptom.png)

* **Relationship between the bugs:**
* After the specified improvement to this test case, we are able to successfully find and get the correct output of `[https://something.html, some-thing.html]` as the following picture:
![Image5](Week4/Test1success.png)

### Test 2: Image contained test
> This breaking test is appearing when we insert the images among the syntax of links.
![test2case](Week4/Test2case.png)


* Code changes:

![test2code](Week4/test2code.png)

* [Here](https://github.com/ericsun153/markdown-parser/blob/main/test3.md) is the link to my breaking test case 2 of **Containing Image**.

* Symptom:

![image4](Week4/test2symp.png)

* **Relationship between the bugs:**
* After the specified improvement to this test case, we are able to successfully find and get the correct output of `[some-thing.html]` as the following picture:
![Image5](Week4/test2success.png)

### Test 3: More complicated and general cases
> 
