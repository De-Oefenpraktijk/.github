# Document Overview
This document explains how we have set up our backend and frontend CI.

# Frontend CI
For the frontend CI we use:
- Build node 16
- Build node 18
- SonarCloud
- Cypress End to End

Links:
- SonarCloud: https://sonarcloud.io/summary/new_code?id=De-Oefenpraktijk_Frontend
- Cypress: https://cloud.cypress.io/projects/qv89m8/


# Backend CI
For the backend CI we use:
- Build
- Test (Unit)
- SonarCloud
- Cypress End to End

Links:
- SonarCloud: https://sonarcloud.io/organizations/de-oefenpraktijk/projects
- Cypress: https://cloud.cypress.io/projects/qv89m8/

# DevOps Flow
![Alt text](../devopsci.png "Optional title")

# To Be Done
- Frontend CI
    - SonarCloud quality gate is now set to a dummy gate. There is a proper gate named "Project QGate". It has to be applied and the bugs need to be fixed. (I know right, we left you all the bugs. Sorry, there truly wasn't enough time for that.) 
    - End-to-end tests have not been made. We only established the connection between cypress and the project. There is a folder in the Frontend repo "cypress/integrations" where when tests are added, they will run automatically.
- Backend CI
    - Unit tests haven't been made, we have set up the automation for them. The automation is working only for Profile Service, you will need to duplicate the logic in the rest of the services. The path to unit tests in Profile service is: "Profile_Service.XUnit/Profile_Service.XUnit.csproj".
    - Unfortunately, the SonarCloud story is the same for the backend as it was in the frontend. One thing to bear in mind. SonarCloud for backend currently only works in main branch. For a reason that we couldn't pinpoint, it doesn't work for other branches. It finds the branches and folders but won't analyze the code. 


# Recommendations and Best Practices

- Make sure that the CI pipeline acts like your safety net. It should prevent you from deploying unstable code. Write tests only where they add value. 