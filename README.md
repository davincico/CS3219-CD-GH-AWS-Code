# Backend Address Book JS - CD
The backend is equipped with basic functionalities, including the ability to add, retrieve, edit, and delete information, by connecting to  MongoDB Atlas.

### Setting up
```
nvm list
nvm use <version>

cd project_working_dir
npm install # install all dependencies

npm install mongodb
```

### Set up MongoDB Atlas 
By using the cloud database, you are now testing the application in a local deployment scenario without using alocal database.
Set up account here: https://cloud.mongodb.com/
- Enter username and password for your database
- Obtain connection string and store in .env (this will contain your username and password as parameters)

Run the application:
```
npm start
```