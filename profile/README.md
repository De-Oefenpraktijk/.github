## Hi there 👋

<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->

# How to use the CD?
There are a couple of things that need to be said about our CD setup
## Backend environment
We use AKS (Azure Kubernetes Service) for our APIs. See https://github.com/De-Oefenpraktijk/Manifest-As-Code for more. As a consequence, the pipelines are designed to deploy to Kubernetes.
## Frontend environment
We chose to deploy the front end with Azure Static Web Apps.  
## DevOps Flow 
Green arrows - developer actions \
Black arrows - automated actions \
![Alt text](/devopsflow.png "Optional title")
## How to use backend CD? 
### Why use staging in the backend?
Staging is a safety net for you as a developer. With staging you can assure that your changes are safe and sound.  
### How to deploy to staging? 
Simply open a pull request from your feature branch to development and GitHub Actions will do the rest.
### How to access the staging environment?
That's a little bit more complex. The idea is that we don't want to expose staging endpoints to the internet. To solve that we decided to use the port-forward functionality of kubetcl (Kubernetes CLI). The way it works is that you forward the traffic from the staging environment in the cluster to your local machine. 
1. Start with logging in to Azure and making sure you have a right Kubernetes context 
2. ```kubectl port-forward service/profile-service 8081:80 -n stage```
3. You can now use ```localhost:8081``` to access the staging environment.
4. You can also use ```localhost:8081/swagger``` to open swagger.
### How to deploy to production?
The next step is to do a code review with your fellow engineers and when your pull request is approved, merge it to the main branch. This will trigger the production pipeline. 
### My changes are disruptive 😰. Can I still roll back?
Yes, you can. Every commit has an associated docker image in the registry. Just revert the commit.
### Where does it fetch k8s manifest from?
There is a folder ```k8s-manifest``` in the root of the folder with the ```deployment.yaml``` file. That file contains the workload definiton.
### How does the pipeline authenticate to Azure?
There is a dedicated service principal account in the resource group RGR-DeOefenpraktijk. Credentials are stored securely in GitHub secrets. The pipeline then authenticates with those credentials to perform actions like build and push images.
### Where can I learn more about AKS Continuous Deployments?
https://learn.microsoft.com/en-us/azure/aks/kubernetes-action







