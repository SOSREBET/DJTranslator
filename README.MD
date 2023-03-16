## Introduction

The purpose of creating this script is to automate the translation of django replicas through Google Translate **without an API**. You can customize / edit the code for yourself.

The script is based on selenium 4.8 and python 3.9.

## Main features

- Selenium + fake-useragent
- Google Translate without API
- Chromedriver
- PEP8
- Multiprocessing mode
- Save python formatting strings
- Save classes of html strings

## Getting Started

1. Clone the repository from Github and switch to the new directory:

```bash
(venv) foo@bar:~$ git clone https://github.com/SOSREBET/DJTranslator.git
(venv) foo@bar:~$ cd DJTranslator/
```

2. Download the appropriate [version](https://chromedriver.chromium.org/downloads) of chromedriver for your Chrome and extract it in DJTranslator.
   
3. Create a virtual environment and activate it:

```bash
foo@bar:~/DJTranslator$ python3.9 -m venv venv
foo@bar:~/DJTranslator$ source venv/bin/activate
```

4. Install project dependencies:
   
```bash
(venv) foo@bar:~/DJTranslator$ pip install -r requirements.txt
```

5. Edit translator.py to change the argument values when running the manager function. Run translator.py.

## How it works

The translator function opens locale_path/code/LC_MESSAGES/django.po and iterates over each line. Each string is checked with the check_translated function (if the string is a django replica, it checks for an existing translation), untranslated strings will be passed to the translate function which will return their translation via GT, after which the string will be written along with its translation.

> The code called Simple string refers to a string that fits on one line in msgid
Complex string - a string that does not fit on one msgid line

## Usage

Translation is done using manger.<br>
The manager takes the following arguments:

- codes: Language codes
- driver_path: Path to chromedriver
- locale_path: Path to locale folder
- headless: Windowless Mode
- multi: Multiprocessor mode
- multi_max: Maximum number of processes
- lang_interface: Language (code) in which GT will be opened
- from_lang: Language code from which the translation will be carried out
- retry: Attempts to translate

<br>

If your GT does not have time to translate, you can increase the first value (1.8) and the second (2.1) in random_pause.

### *My unsuccessful attempts to improve the script*

1. Run entire script via Class:<br>
   I tried to implement a single Class, but driverChrome is non-serializable, as a result of which multiprocessing stops working.
2. Implement large line breaks django.po:<br>
   It was possible to implement these transfers, but because of this, the stability and quality of the translation deteriorated. I've tried different ways, and in the end I can say this: if you really need hyphens, try to implement them through the maximum length of the line.
