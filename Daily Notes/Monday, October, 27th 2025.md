Creator Realm Standup Meeting Notes
Monday 27  October 2025

David Adelesi and team members discussed progress and plans for the week. David worked on the front end and back end, including setting up email notifications using AWS SES due to SendGrid's limitations. Ojabo John faced deployment challenges due to unavailability but plans to deploy services soon. Ajibewa Daniel completed user and profile creation, API gateway setup, and Docker files. They discussed using a single Redis and RabbitMQ server for cost efficiency, with plans to scale later. The team emphasized the need for technical documentation and a separate testing environment before production deployment. Daniel will focus on the payment service, while David will continue front-end development.

  

Transcript

https://otter.ai/u/kDzK2QyOazKz8flOmWNc_RZR3nc

  

Action Items

• [] Ojabo John to deploy the services, coordinating with Edina.

• [] Daniel Ajibewa to complete the work on the Odd service and user service, and start working on the payment service.

• [] David Adelesi to continue working on the front-end, including the client-side aspects.

• [] The team to collaborate on creating a technical documentation for the platform and individual microservices.

• [] The team to set up a separate testing/staging environment before production deployment.

  

Outline

Progress and Updates from the Previous Week

• David Adelesi acknowledges the progress made despite being behind schedule and appreciates everyone's participation and commitment.

• David Adelesi worked on the front end midweek and researched backend requirements, including setting up email notifications and communicating with Mr. Austin for official emails.

• The plan to use SendGrid for email notifications changed to AWS SES due to SendGrid's limitations in the free version.

• David Adelesi also spoke with a mentor for ideas and took notes that might be useful in the future.

Ojabo John's Update and Challenges

• Ojabo John mentions he didn't do much last week due to unavailability and the need for coordination with Mr. Edina.

• David Adelesi notes that Mr. Edina was busy preparing for a startup event, which affected her availability.

• Ojabo John expresses a desire to deploy everything together to ensure consistency.

• David Adelesi emphasizes the importance of collaboration and coordination to move things forward.

Ajibewa Daniel's Contributions and Plans

• Ajibewa Daniel worked on the back end, setting up the API gateway, and working on the odd services, including login, logout, and email functionality.

• He completed user and profile creation for the user service but hasn't onboarded clients yet.

• Ajibewa Daniel also worked on Docker files for various services and ensured they are running.

• He plans to focus on the payment service at the end of the week, depending on the progress of other services.

Discussion on API Gateway and Routing

• Ojabo John asks for clarification on how the API gateway works and how requests are routed.

• Ajibewa Daniel explains that the front end sends requests through the API gateway, which then routes them to the respective microservices.

• The routing is handled by a proxy library, and the setup was tested successfully on the local machine.

• David Adelesi and Ajibewa Daniel discuss the use of Redis and RabbitMQ, deciding to use one instance of each for now to keep costs low.

Plans for Deployment and Testing

• David Adelesi emphasizes the importance of having a separate environment for testing before moving to production.

• Ojabo John agrees, noting that it's crucial to avoid pushing bugs directly to production.

• David Adelesi plans to continue working on the front end and integrate services for testing.

• Ajibewa Daniel will focus on completing the odd service and starting the payment service, depending on the progress of other services.

Final Remarks and Next Steps

• David Adelesi thanks everyone for their contributions and emphasizes the importance of collaboration and clear communication.

• He mentions a follow-up meeting with Ajibewa Daniel and Ojabo John to keep things in sync.

• The team agrees to stay in touch and work on their respective tasks for the week.

• The meeting concludes with everyone expressing their commitment to a productive week.