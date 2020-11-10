![](doc/landing.png)

Digits is a web application that allows users to:

  * Register an account to store contacts.
  * Create and manage their contacts.
  * Add notes to individual contacts with timestamps.

## Installation

First, [install Meteor](https://www.meteor.com/install).

Second, [download a copy of Digits](https://github.com/jackiewong99/digits). **The Digits repo is private and a request for permission to gain access from the author is required.**

Third, go to your newly created repository, and click the "Clone or download" button to download your new GitHub repo to your local file system.  Using [GitHub Desktop](https://desktop.github.com/) is a great choice if you use MacOS or Windows.

Fourth, cd into the app/ directory of your local copy of the repo, and install the required libraries with:

```
$ meteor npm install
```

## Running the system

Once the libraries are installed, you can run the application by invoking the "start" script in the [package.json file](https://github.com/ics-software-engineering/meteor-application-template-react/blob/master/app/package.json):

```
$ meteor npm run start
```

The first time you run the app, it will create some default users and data. Here is the output:

```
meteor npm run start

> meteor-application-template-react@ start /Users/philipjohnson/github/ics-software-engineering/meteor-application-template-react/app
> meteor --no-release-check --settings ../config/settings.development.json

[[[[[ ~/github/ics-software-engineering/meteor-application-template-react/app ]]]]]

=> Started proxy.
=> Started MongoDB.
I20180227-13:33:02.716(-10)? Creating the default user(s)
I20180227-13:33:02.742(-10)?   Creating user admin@foo.com.
I20180227-13:33:02.743(-10)?   Creating user john@foo.com.
I20180227-13:33:02.743(-10)? Creating default data.
I20180227-13:33:02.743(-10)?   Adding: Basket (john@foo.com)
I20180227-13:33:02.743(-10)?   Adding: Bicycle (john@foo.com)
I20180227-13:33:02.743(-10)?   Adding: Banana (admin@foo.com)
I20180227-13:33:02.744(-10)?   Adding: Boogie Board (admin@foo.com)
=> Started your app.

=> App running at: http://localhost:3000/
```


### Note regarding "bcrypt warning":

You will also get the following message when you run this application:

```
Note: you are using a pure-JavaScript implementation of bcrypt.
While this implementation will work correctly, it is known to be
approximately three times slower than the native implementation.
In order to use the native implementation instead, run

  meteor npm install --save bcrypt

in the root directory of your application.
```

On some operating systems (particularly Windows), installing bcrypt is much more difficult than implied by the above message. Bcrypt is only used in Meteor for password checking, so the performance implications are negligible until your site has very high traffic. You can safely ignore this warning without any problems during initial stages of development.

### Note regarding "MongoError: not master and slaveOk=false":

Intermittently, you may see the following error message in the console when the system starts up:

```
MongoError: not master and slaveOk=false
     at queryCallback (/Users/philipjohnson/.meteor/packages/npm-mongo/.3.1.1.1mmptof.qcqo++os+web.browser+web.browser.legacy+web.cordova/npm/node_modules/mongodb-core/lib/cursor.js:248:25)
     at /Users/philipjohnson/.meteor/packages/npm-mongo/.3.1.1.1mmptof.qcqo++os+web.browser+web.browser.legacy+web.cordova/npm/node_modules/mongodb-core/lib/connection/pool.js:532:18
     at _combinedTickCallback (internal/process/next_tick.js:131:7)
     at process._tickDomainCallback (internal/process/next_tick.js:218:9)
```

While irritating, this message appears to be harmless and [possibly related to a race condition between the development instance of Mongo and Meteor](https://github.com/meteor/meteor/issues/9026#issuecomment-330850366). By harmless, I mean that in most cases, the console goes on to display `App running at: http://localhost:3000/` and no problems occur during run time.

### Viewing the running app

If all goes well, the template application will appear at [http://localhost:3000](http://localhost:3000).  You can login using the credentials in [settings.development.json](https://github.com/ics-software-engineering/meteor-application-template-react/blob/master/config/settings.development.json), or else register a new account.

### ESLint

Lastly, you can verify that the code obeys our coding standards by running ESLint over the code in the imports/ directory with:

```
meteor npm run lint
```

## User Interface Walkthrough

#### Landing Page

When you retrieve the app at http://localhost:3000, this is what should be displayed: (A landing page that displays descriptions of the practicality of Digits.)

![](doc/landing.png)

#### Register Page

Alternatively, clicking on the Login link, then on the Sign Up menu item displays this page where the user can create a Digits account:

![](doc/register.png)

#### Login page

Clicking on the Login link, then on the Sign In menu item displays this page where the user can sign into their account:

![](doc/login.png)

#### User Home Page

Once you log in (either to an existing account or by creating a new one), the navbar changes with new functionality as follows while looking similar to the landing page:

![](doc/login_landing.png)

You can now add new contacts, and list the contacts you have created. **Note you cannot see any contacts created by other users.**

#### Add Contact Page

After logging in, here is the page that allows you to add a new contact:

![](doc/addcontact.png)

#### List Contacts Page

After logging in, here is the page that allows you to list all the contacts you have created and create timestamped notes for each contact:

![](doc/listcontacts.png)
![](doc/addnote.png)

You can click the "Edit" link to go to the Edit Contact page, shown next.

#### Edit Contact Page

After clicking on the "Edit" link associated with a contact, this page displays the form that allows you to change and save the contact's information:

![](doc/editcontact.png)

#### Admin Page

The Admin page lists all of the contacts created by all of the users:

![](doc/admin.png)

**Note that non-admin users cannot get to this page, even if they type in the URL by hand.**
