## Git into Flow: Continuous Integration
Tuesday 9:30AM

The players in this session:

1. Heroku
2. Github
3. Git

##Git
As we know, Git is an Open-source distributed version control.

Modern code storage, versioning, basic workflow support
- Repo: a base code storage object
- Distributed: everyone has a copy of the historical repo
- Branches - for features
- Merge - where you more the code.

##GitHub - 9 Million Users
The defacto way to use Git.
Extends Git in meaningful ways.
- Pull Requests is probably the main reason.
- CI (Travis, Circle) integrations, CD Integrations (Heroku NEW)
- Team-oriented.

##Heroku
- PaaS with Salesforce Integration.
- $git push heroku master (The original deploy interface)
- Deploy (automatically) on GitHub push.
- New feature is Heroku Review Apps for Pull requests.
- The Review App will spin up the code and then allow you to test it. 

A GitHub pull request is now spinning up a Heroku review app. 

##New Feature
Enable automatic deploys from github/heroku. 

Recommend creating two different applications, then create a pipeline. Heroku will understand that the apps are related if they are in a pipeline. 