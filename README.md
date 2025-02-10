# Setup

1. Install NodeJS LTS https://nodejs.org/en/download.
2. Install VSCode https://code.visualstudio.com/.
3. Install Git https://git-scm.com/.
4. Clone the Github repository https://github.com/qaware/schueler-hackathon-app.git by executing `git clone https://github.com/qaware/schueler-hackathon-app.git` in a folder of your choosing.
5. Open the cloned repository folder in VScode File -> Open Folder... and select the schueler-hackathon-app folder.
6. Install the recommended Extensions for this Project by selecting the Extensions Tab on the left and typing `@recommended` in the search bar. Then press the *Install Workspace Recommended Extensions*, which is a cloud with an arrow pointing down beneath the search bar.
7. In the bottom of your VScode window you can find a terminal. If there is no terminal open it by pressing Terminal -> New Terminal or strg-shift-ö. Enter `npm install` and execute the command.
8. Install [localtunnel](https://github.com/localtunnel/localtunnel) by entering `npm install -g localtunnel` into the terminal.
9. After the installtion is finished execute `npm run dev` and you should see the UI in any browser under `http://localhost:5173/`.

# Collaboration

This project will be worked on by teams of three to five people. You can enhance your collaboration effort by following these steps:

1. You can quickly work on the same code base with your collegues by using the [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare) plugin. For this to work you need a Microsoft or Github Account. Then simply follow the [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare) Quickstart guide.
2. If you want to quickly expose the app to your colleagues open a new terminal (keep the npm run dev process running in the other terminal) and enter `lt --port 5173`. This will generate a URL which is publicly available. You can find the password under https://loca.lt/mytunnelpassword. This should be done by the Live Share Host so the other people can also see the app on their browser.

# Goals
1. Create a registration page:
* Create a username, password and e-mail field.
* Create a password check with fitting requirements. For example: the password needs at least 8 characters. Make sure to add a hint if the user does enter a valid password.
* Store the information in local storage, so the user is able to login with its created account.
2. Create a landing page
* Be creative fill the app with content. 
* For example use a public Rest API, see https://github.com/public-apis/public-apis for inspiration or create a blog post system where you can see the posts of other users. (You can store the blog posts in local storage as wel)

# Stretch Goal
Make a real app with backend and database:
* Create a backend folder. Install Python and follow the [FastAPI Installation](https://fastapi.tiangolo.com/#installation) guide. Create the python files in the backend folder.
* Refactor the login to call the backend via REST (for example by using axios) and store the users in a database: https://fastapi.tiangolo.com/tutorial/sql-databases/. You can startup a local Postgres database with docker: https://hub.docker.com/_/postgres


# Resources
## HTML, Javascript and CSS basics
* HTML, CSS, JavaScript: https://www.w3schools.com/, https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web
* CSS selectors: CSS Diner https://flukeout.github.io/
* CSS flexbox: https://flexboxfroggy.com/#de
* CSS https://codingfantasy.com/games
* CSS flexbox http://www.flexboxdefense.com 

## Vue
* VueJS documentation: https://vuejs.org/guide/introduction.html

## Tailwind
* TailwindCSS documentation: https://tailwindcss.com/docs/flex-basis
