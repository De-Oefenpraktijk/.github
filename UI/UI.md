# Document Overview
This document explains the why's and hows of the frontend UI.

# Why React
The research about the frontend choice can be seen in the project files (in teams files) in researches -> Optimal framework choice.

# How to deploy
The deployment of the front end is pretty straight forward. Every time the main branch is changed, a GitHub action is activated which deploys the frontend. 

# Recommendations and Best Practices

- In the repo's README.md you can find some rules for the repo. You as a group can come up with new rules and overwrite the existing ones.
- When you want to test a change, create a merge request to the main branch (do not approve it). Then a staging domain will be created where you can test if the changes are working as planned. Using the stage environment can prevent deploying bugs in production.
