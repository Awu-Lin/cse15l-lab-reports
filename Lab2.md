## my code
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/3888ae7d-b9f7-4b16-86c4-6d50f4f70e8b)
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/577cb68e-8670-47d9-b253-5c7bf08ad966)


## When enter the command `localhost:4000/add-message?s=Hello`:
![GVLYSJU%7X3OE)~1 NQGWO2](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/5c0f937f-73c1-4aa9-bab6-44460053db17)
Or Using CURL commannd
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/ecccdc07-2be4-41c6-9e0b-c853a08763e5)


### 1. Which methods are called in the code?
The `handleRequest` method is called.

### 2. What are the parameters associated with those methods and the values of any associated fields of the class?
- The value of the parameter `url` for the `handleRequest` method is `localhost:4000/add-message?s=Hello`, which is a URI object.
- The relevant fields of class `StringHandler` are:
  - `str`: its initial value is an empty `StringBuilder` object.
  - `count`: its initial value is 0.

### 3. How do the values of the relevant fields of the class change as a result of this particular request? If no values were changed, explain why.
- The value of `count` increases from 0 to 1 as the request is processed.
- The value of `str` changed from an empty `StringBuilder` object to a `StringBuilder` object containing "1. Hello\n".
- This is because the logic inside the `handleRequest` method checks to see if the path of the request is `/add-message`, and if it is, it takes the message from the query string, adds it to `str`, and increases the value of `count`.


## When enter the command `localhost:4000/add-message?s=How%20are%20you`:
![RTYSH{@L9%7FOJ$D%Z3FSQV](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/e68dede5-bc9e-4781-8971-cb1eb1e6c1bd)
Or Using CURL commannd
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/b44b3f7b-81fa-47dd-886c-5e15deb4a5f4)

### 1. Which methods are called in the code?
The `handleRequest` methods are called.

### 2. What are the parameters associated with those methods and the values of any associated fields of the class?
- The value of the `handleRequest` method's parameter `url` is `localhost:4000/add-message?s=How%20are%20you`, which is a URI object.
- The relevant fields of class `StringHandler` are:
  - `str`: Before this request, its value was a `StringBuilder` object containing "1. Hello\n".
  - `count`: Before this request, its value was 1.

### 3. How do the values of the relevant fields of the class change as a result of this particular request?
- When the request is processed, the value of `count` is increased from 1 to 2.
- The value of `str` changes from a `StringBuilder` object containing "1. Hello\n" to a `StringBuilder` object containing "1. Hello\n2. How are you\n".
- This is because the logic inside the `handleRequest` method checks to see if the path of the request is `/add-message`, and if it is, it gets the message from the query string, adds it to `str`, and increases the value of `count`.

### Part 2
![MALR9DUA(D1P R`JDN2 ZVP](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/465e4b99-c243-4888-830f-b5e45f1b401c)
## The path to the private key for your SSH key for logging into ieng6 (on your computer or on the home directory of the lab computer)
- Base on the imformation in photo, the path for private key is `/home/linux/ieng6/cs151fa23/cs151fa23cs/.ssh/id_rsa`
## The path to the public key for your SSH key for logging into ieng6 (within your account on ieng6)
- Same as last problem, use the information in phtot we know that the public key for SSH is `/home/linux/ieng6/cs151fa23/cs151fa23cs/.ssh/id_rsa.pub`
## A terminal interaction where you log into ieng6 with your course-specific account without being asked for a password.
![image](https://github.com/Awu-Lin/cse15l-lab-reports/assets/94472422/98b606fa-c4ad-4854-92c7-08b48482b67b)
- base on what phtot shows, I enter into my accont successfully without enter password.

### Part 3
- During the week I learned how to use ssh related commands, including starting a service, using code to set up the content of the service, and editing web pages. On the other hand I learned to create private and public keys and use them to authenticate my computer.
