# Pikaptcha
Based off pikapy by skvvv, which is based off ptc2 Kitryn, which is based off ptcaccount by jepayne1138, etc.
Also uses pogoapi from keyphact

## Description
Pikaptcha creates PTC accounts by creating a chrome session and automatically entering data in the required fields. If you choose to use the 2captcha service, the entire script can be run automatically, else you will need to manually solve captchas.
Pikaptcha creates the PTC account and completes the TOS in game. It does NOT verify emails. See below for a script to verify emails by using the plusmail trick.

## Installation
**For Windows**
Install the following clickable links: (if you cannot click them, all links are at the bottom.)
1. [Google Chrome](https://www.google.com/chrome/) installed to default directory in C:\

2. [Python 2.7.12](https://www.python.org/downloads/release/python-2712/). Do this during setup.

3. [Git](https://git-scm.com/download/win). Do this during setup.

4. [Microsoft Visual C++ Compiler for Python 2.7](https://www.microsoft.com/en-ca/download/details.aspx?id=44266)

5. Shift+Right Click your desktop and "Open command window here".

6. Type `path` and hit enter. You should see C:\Python27, C:\Python27\Scripts, and C:\Program Files\Git\cmd

7. [Download Chromedriver](http://chromedriver.storage.googleapis.com/2.23/chromedriver_win32.zip). Unzip the file and place it in C:\Python27\Scripts

8. Shift+Right Click your desktop and "Open command window here".

9. Type `pip install git+https://github.com/sriyegna/pikaptcha` and hit enter

10. Type `pip install git+https://github.com/keyphact/pgoapi.git` and hit enter

11. Refer to "How To Use" instructions below


**For OSX**

1. Open terminal and install chromedriver by typing `brew install chromedriver`

2. In terminal type `pip install git+https://github.com/sriyegna/pikaptcha` without quotations and hit enter

3. In terminal type `pip install git+https://github.com/keyphact/pgoapi.git` without quotations and hit enter

4. Refer to "How To Use" instructions below


**For Debian based linux**

1. Open terminal and install chromedriver by typing `sudo apt-get install chromium-browser`

2. In terminal type `pip install git+https://github.com/sriyegna/pikaptcha` without quotations and hit enter

3. In terminal type `pip install git+https://github.com/keyphact/pgoapi.git` without quotations and hit enter

4. Refer to "How To Use" instructions below

If an update is made to pikaptcha, all you need to do to update is open CMD or terminal and type
    `pip install --upgrade git+https://github.com/sriyegna/pikaptcha`

If you want to uninstall pikaptcha, all you need to do to uninstall is open CMD or terminal and type
    `pip uninstall pikaptcha`
	
## Using 2captcha
If you want to use the 2captcha service (if you cannot click the links, they are also at the bottom of the readme)

1. [You need to sign up here](https://2captcha.com/auth/register)

2. [Verify your email (if needed) and login](https://2captcha.com/auth/login)

3. Either work (Start Work on top) or deposit money (Deposit on left). Get a balance or you will have no credit to solve captchas

4. Click the "2Captcha API" tab at the top

5. Look for captcha KEY. There should be a long string after that like a6ebcb3f4a7b6f6e319d8e1c37e25ec4

6. For the rest of the guide %YOUR_2CAPTCHA_KEY%=the string you found there


## How to use
Shift+Right Click your desktop and "Open command window here". OR open Terminal if on linux/osx. Note that usernames.txt (the file with the accounts) will be made on your desktop, or wherever you ran terminal/cmd from. To run pikaptcha, just type `pikaptcha` into the cmd/terminal. See examples below.

You can type `pikaptcha --help` to see all parameters. Optional parameters are as follows.
```
	--username, -u #This is the username
	--password, -p #This is the password
	--email, -e #This is the email
	--count, -c #This is the number of accounts to make
	--recaptcha, -r #This is your 2captcha key
```

Example 1 : Create an entirely random account by manually entering the captcha yourself

```
pikaptcha
```

Example 2 : Create an entirely random account with automated captcha solving

```
pikaptcha -r %YOUR_2CAPTCHA_KEY%"
When you enter your 2captcha key, it will look something like
pikaptcha -r a6ebcb3f4a7b6f6e319d8e1c37e25ec4"
```
	
Example 3 : Create 10 entirely random accounts by manually entering the captcha yourself

```
pikaptcha -c 10
```
	
Example 4 : Create 10 an entirely random accounts with automated captcha solving	

```
pikaptcha -c 10 -r %YOUR_2CAPTCHA_KEY%
When you enter your 2captcha key, it will look something like
pikaptcha -c 10 -r a6ebcb3f4a7b6f6e319d8e1c37e25ec4
```

Example 5 : Create 10 random accounts that have the same set password=PaSsWoRd by manually entering captcha

```
pikaptcha -c 10 -p PaSsWoRd
```

Example 6 : Create 1 account that has a specific username=UsErNaMe with automated captcha solving

```
pikaptcha -u UsErNaMe -r %YOUR_2CAPTCHA_KEY%
```

Example 7 : Create 10 accounts using a single email address (read below on plusmail for more info) with automated captcha solving

```
pikaptcha -p PaSsWoRd -c 10 -m emailaddress+@gmail.com -r %YOUR_2CAPTCHA_KEY%
```
	
The PlusMail trick work as follows. Suppose your name is Mark and you own Mark@gmail.com as your email account. If I send an email to Mark+Jacob@gmail.com, it will still go to Mark@gmail.com. Similarly, if I send an email to Mark+asldksdjek@gmail.com, it will go to Mark@gmail.com. The PlusMail trick takes advantage of the fact that Niantic doesn't check that there isn't a difference between Mark and Mark+Jacob because not all email providers support this. When you use "-m mark+@gmail", it will generate emails like Mark+asdkjs@gmail.com differently for each account creation, but all emails will go to Mark@gmail.com
	
To verify all emails in one swoop, you can use this [script by Sebatienvercammen](https://gist.github.com/sebastienvercammen/e7e0e9e57db246d7f941b789d8508186)
	   
	  
## Common Issues
If you are still having troubles, you can join us at [discord channel](https://discord.gg/VvwyS) https://discord.gg/VvwyS
Please let us know what your issue is, instead of just saying it doesnt work. Copying the error code you receive is very helpful.

- Cannot find chrome binary. Chrome should be installed to the default directory in C. Ensure that it is. If it is, try uninstalling and reinstalling.

- Cannot find PgoApi module. `pip install git+https://github.com/keyphact/pgoapi.git`

- Chromedriver not found. Your chromedriver.exe file is either not in C:\python27\scripts OR you did put the file there but you do not have an environment path setup for C:\python27\scripts

- pip is not recognized as an internal or external command. You do not have an environment path setup for C:\python27\scripts OR python 2.7.12 is not installed

- git is not recognized as an internal or external command. You did not install GIT

- selenium not found `pip install selenium`

## Links
- Google Chrome https://www.google.com/chrome/

- Python 2.7.12 https://www.python.org/downloads/release/python-2712/

- Git https://git-scm.com/download/win

- Microsoft Visual C++ Compiler for Python 2.7 https://www.microsoft.com/en-ca/download/details.aspx?id=44266

- Download Chromedriver http://chromedriver.storage.googleapis.com/2.23/chromedriver_win32.zip

- 2 Captcha Signup https://2captcha.com/auth/register

- 2 Captcha login https://2captcha.com/auth/login

- Email verify script by Sebastienvercammen https://gist.github.com/sebastienvercammen/e7e0e9e57db246d7f941b789d8508186