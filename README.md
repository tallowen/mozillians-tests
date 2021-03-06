Mozillians Tests
===================

Automated tests for the Mozillians web application.

Running Tests
-------------

### Java
You will need a version of the [Java Runtime Environment][JRE] installed

[JRE]: http://www.oracle.com/technetwork/java/javase/downloads/index.html

### Python
Before you will be able to run these tests, you will need to have Python 2.6 installed (or a newer, stable version).

Run

    easy_install pip

followed by

    sudo pip install -r requirements/mozwebqa.txt

__note__

If you are running on Ubuntu/Debian you will need to do following first


    sudo apt-get install python-setuptools

to install the required Python libraries.

### Selenium
Once this is all set up, you will need to download and start a Selenium server. You can download the latest Selenium server from [here][Selenium Downloads]. The filename will be something like 'selenium-server-standalone-x.x.x.jar'

To start the Selenium server run the following command:

    java -jar ~/Downloads/selenium-server-standalone-x.x.x.jar

Change the path/name to the downloaded Selenium server file.

[Selenium Downloads]: http://code.google.com/p/selenium/downloads/list

### py.tests

Tests are run using **py.tests**. It will automatically find the tests to be run when run in the root of [mozillians-tests][github]. The following are the options that you will need to configure in order to run the tests appropriately.

- **credentials:** The path to a yaml file that stores usernames and passwords to log into browserID.
- **api:** Currently mozillians tests are set to the rc api. 
- **baseurl:** The URL where you can locate the mozillians instance you are testing. Likely either http://mozillians-dev.allizom.org or http://localhost:8001.
- **browser:** Configure the browser that selenium will talk to. In this case "*firefox"
- **n:** The number of simultaneously running tests.

[github]: https://github.com/tallowen/mozillians-tests

### Credentials.yaml
Take the credentials file in the root directory and replace the emails and passwords with valid browserID emails and passwords. Make sure that the vouched email account is infact vouched on the test server. Here is the example credential file:

    user:
        email: <insert valid email>
        password: <insert valid password>
        name: <give it a name>

    unvouched:
        email: <insert valid email>
        password: <insert valid password>
        name: <give it a name>

Before you get started make sure to update the fields in between "<" and ">".

### Running tests locally

To run tests locally, it's a simple case of calling py.test from the Mozillians-tests directory.

Try running a command as follows and modifying it as necessary.

    py.test -n 2 --credentials=credentials.yaml --baseurl=http://mozillians-dev.allizom.org --browser=*firefox 


For other instructions type py.test --help .


Writing Tests
-------------
If you want to get involved and add more tests then there's just a few things
we'd like to ask you to do:

1. Use the [template files][GitHub Templates] for all new tests and page objects
2. Follow our simple [style guide][Style Guide]
3. Fork this project with your own GitHub account
4. Make sure all tests are passing, and submit a pull request with your changes

[GitHub Templates]: https://github.com/AutomatedTester/mozwebqa-test-templates
[Style Guide]: https://wiki.mozilla.org/QA/Execution/Web_Testing/Docs/Automation/StyleGuide

License
-------
This software is licensed under the [Mozilla Tri-License][MPL]:

    ***** BEGIN LICENSE BLOCK *****
    Version: MPL 1.1/GPL 2.0/LGPL 2.1

    The contents of this file are subject to the Mozilla Public License Version
    1.1 (the "License"); you may not use this file except in compliance with
    the License. You may obtain a copy of the License at
    http://www.mozilla.org/MPL/

    Software distributed under the License is distributed on an "AS IS" basis,
    WITHOUT WARRANTY OF ANY KIND, either express or implied. See the License
    for the specific language governing rights and limitations under the
    License.

    The Original Code is Mozilla WebQA Selenium Tests.

    The Initial Developer of the Original Code is Mozilla.
    Portions created by the Initial Developer are Copyright (C) 2011
    the Initial Developer. All Rights Reserved.

    Contributor(s):

    Alternatively, the contents of this file may be used under the terms of
    either the GNU General Public License Version 2 or later (the "GPL"), or
    the GNU Lesser General Public License Version 2.1 or later (the "LGPL"),
    in which case the provisions of the GPL or the LGPL are applicable instead
    of those above. If you wish to allow use of your version of this file only
    under the terms of either the GPL or the LGPL, and not to allow others to
    use your version of this file under the terms of the MPL, indicate your
    decision by deleting the provisions above and replace them with the notice
    and other provisions required by the GPL or the LGPL. If you do not delete
    the provisions above, a recipient may use your version of this file under
    the terms of any one of the MPL, the GPL or the LGPL.

    ***** END LICENSE BLOCK *****

[MPL]: http://www.mozilla.org/MPL/
