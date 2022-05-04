Python Polls
This is a live survey/poll app.

Initial Plan
Anyone can vote
Anyone can add an option to the poll (during a certain time period)
The options can just be a picture (uploaded would be nice, but even just as a link to an image URL would be okay)
Can use social login from Twitch or Github
Basically, let people make suggestions or requests, and then let everyone else vote on those suggestions/requests

For example. If I were to do a "Build this thing in CSS" challenge on Twitch, I'd want people to be able to suggest screenshots, and for people to vote on which one they'd like to see.

Requirements
Poll owner (person who created the poll):

Create a poll
Toggle the option to allow people to add options to the poll (they can toggle off and on when they want)
Can allow voting to start
Can choose to time the voting or manually turn off and on
Can give other people roles, like mod
Can log in with Twitch
Mod (bonus feature?):

Can remove poll choices
Can vote
Poll voters (people who participate in a poll):

Anyone can vote
Anyone can add an option to the poll (during a certain time period)
Don't need to be logged in unless they are adding options to the poll
Technologies
Python 3.9+
Poetry
Fast API
Postgres
SQLAlchemy
Uvicorn
Local Development
Clone this repo and cd into repo directory
Check your Python version: python -V. If less than 3.9, use pyenv to install and switch to 3.9+.
Make sure Poetry is installed
Create a virtual environment: python -m venv venv
Install dependencies: poetry install
Run the server: poetry run uvicorn main:app --reload
Access swagger at: http://127.0.0.1:8000/docs
Schema
User

username
email
create_at
updated_at
Poll

title
type: ChoiceField (e.g. text or image)
created_by
create_at
updated_at
is_add_choices_active
is_voting_active
Choice

poll_id
text
image (nice to have feature)
votes
created_by
create_at
updated_at
Moderator

mod_for
mod_user
create_at
updated_at
Ban

poll_owner_id
banned_by (poll owner or moderator)
user_id (person who is banned)
create_at
updated_at
Design API
// TODO: social auth endpoints

polls/

GET: list of the users polls
POST: create a new poll
DELETE: all polls???
polls/:id/

GET
PATCH
DELETE
polls/:id/choices/

GET
POST
polls/:id/choices/:id/

GET
PATCH
DELETE
banned-users/

GET
users/:id/ban/

POST
DELETE
users/:id/mod/

POST
DELETE
Planning TODOs
 List all requirements
 Create schema
 Design API
 Create mockups
 Choose technologies
