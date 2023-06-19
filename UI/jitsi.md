# Document Overview
This document explains why, why it was chosen, and how it can be used.

# What is Jitsi
Jitsi is an open-source platform for video conferencing, online meetings, and real-time communication. It provides a set of tools and libraries that allow developers to integrate video conferencing capabilities into their applications or build their own video conferencing solutions. Jitsi offers features such as multi-party video calls, screen sharing, chat functionality, and more. It aims to provide secure and privacy-focused communication options, making it a popular choice for various applications and projects.

# Why Jitsi
We made documented research about the different options for video calling solutions in the Oefenpraktijk system. We compared Teams, Zoom, custom implementation, and Jitsi. Jitsi was the chosen option because it was the only option that is open-source and can be deployed by ourselves. 
- Key factors
  - Has a free version - meet.jit.si which can be used in development - https://meet.jit.si/
  - Can be self-hosted - https://jitsi.github.io/handbook/docs/devops-guide/devops-guide-manual/

# How to use
As mentioned Jitsi can be used with a free version and when deployed.
- Free version  
  - Right now the Frontend repo is configured to use the free version. 
- Self-deployed version
  - We have decided to self-host Jitsi in a VM in Azure currently called 'Jitsi'. https://www.youtube.com/watch?v=OhgvC0gPbKw This tutorial was used to deploy it. The machine is currently stopped to not spend money. 
  - To connect the Jitsi VM to the frontend you just have to start the VM and in the frontend open RoomPage.jsx, find the JitsiMeeting component, and add the following string into the component: 'domain="jitsivm04upscqlb9.westeurope.cloudapp.azure.com"'

# To Do
- When we first set up Jitsi, we made it work with the deployed version. Unfortunately, we discovered that a problem occurs when the deployed version is used. The observed problem is that a video and microphone can not be transmitted. We estimate that the problem is in the VM or in the Jitsi instance in the VM.
- When the Jitsi bug is fixed, you should further test what is working, what config settings of Jitsi should be changed, etc. Align with the PO for the Jitsi features.  


# Recommendations and Best Practices

- Use the free version of Jitsi (meet.jit.si) when developing. In the meanwhile, make sure that the deployed version works as expected. That way you can be sure that you have a deployed version without spending the costs when the project is still in the development process.
