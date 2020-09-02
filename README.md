# CovidBot-RASA
RASA based covid bot on flask

## Python environment
 
  - Create a python virtual environment
  - Activate the virtual environment
  - All the commands to be run in the virtual environment

## Rasa set up 
 
### Install rasa

  - pip install rasa
  - Alternatively, execute the requirements.txt from the repo

### Initiate rasa

   - Clone this project if you don't want to initiate rasa on your own.
   - Alternatively, create an empty directory where you want to the project to live
   - Cd  into your project directory
   - Command to initiate rasa :  *rasa init*
   - This will create all the basic files

### Add Covid specific intents and entities to data/nlu.md

   - corona_state is a project specific intents
   - Other intents comes with *rasa init*  

### Add actions in data/stories.md
   
   - Add a new story to connect the new intent corona_state to new action
   - new action name is action_corona_tracker

### Add action in domain.yml

   - Add a new action : action_corona_tracker

### Ensure endpoints in endpoints.yml

   - Ensure the endpoints are uncommented in endpoints.yml
   - action_endpoint points to localhost at port 5055

### Add custom actions to actions.py

   - Actual logic of the tracker happens here.
   - Tracker has the inputs to the custom function
   - Dispatcher gives back the output

## Flask set up

### Flask entry file : app.py

   - If you had executed requirements.txt, flask should be already there
   - Else install it using *pip install flask*
   - app.py is the flask entry point
   - app.py interacts with the rasa endpoint
   - app.py renders the output to a html page

### UI page at templates/index.html

   - Accepts simple text input from app.py

## How to run the set up

### Train rasa

   - Run command *rasa train* at the project folder
   - This should create a new model file under models directory
   - Train and regenerate whenever changes to rasa specific files are made 

### Create an action server

   - Custom actions require a seperate server to execute on
   - Command to create action server *rasa run actions*
   - Keep the action terminal open to allow the action server to live

### Run rasa

   - Open a new terminal and run rasa with api
   - *rasa run -m models --enable-api*
   - Keep this rasa terminal open as well

### Run flask

   - To run flask execute *run flask*

