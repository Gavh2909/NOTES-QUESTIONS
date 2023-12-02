# Jenkins : 

## Realtime Application Environments

 ### DEV env : Developers will use to perform code integration testing

 ### QA env : Testers will use to perform functional testing

 ### UAT env : User acceptance testing  (client side team will perform application testing )

 ### Pilot env : It is also called as Pre PRoduction environment (performance testing)

 ### Prod env : Live environment. End user can access and use application running on PROD env.

           www.facebook.com -> production env of the project

## TEAMS : 

 ### DEVELOPMENT : Responsible for project Development (Coding)

 ### TESTING : Responsible for project functionality testing (verification and validation)

 ### OPERATIONS : Responsible for build and deployment process.


## [ DEV + OPS ====> DevOps ]

 - DevOps is a process is used to collloborate development team and operations team work.
 
 - Using DevOps process we can simplify application build and deployment process.

## Build and Deployment Process :

### Build Process: 
  
  1. Source Code Management(SCM):
     Developers work with version control systems (e.g. Git) to manage and track changes in source code.
  
  2. Continous integration (CI):
     Code changes trigger automated build processes through CI tools (e.g. Jenkins, GitLab CI, Travis CI).
     CI ensures that the codebase is consistently integrated and builds successfully.
  
  3. Build Tools:
     -Build Tools (e.g. Maven, Gradle for java; npm, webpack for javascript) compile source code, manage dependencies,
      and create executeble artifacts.
  
  4. Unit Testing:
     - Automated unit tests are executed during the build process to validate code correctness at the individual componenr level.
  
  5. Static Code Analysis:
     -Tools like SonarQube or ESLint analyse code statically to identify potential issues, code smells, and ensure
      adherence to coding standards.
  
  6. artifact Management:
     -Build artifacts (e.g. JAR files, binaries) are stored in a Repository (e.g. Nexus, Artifactory) for versioning and reuse.

### Deployment Process:
  1. Continous Deployment(CD):
     -Continous Deployment automates the deployment of successfully built artifacts to target Environments.
     -Alternatively, some projects use Continous Delivery, where deployment to production are triggered manually after successful builds.
  
  2. Environment Configuration;
     -Deployment Configurations including environment-specific parameters, are managed using tools like Ansible, Puppet or CHef.
  
  3. Containerization:
     - Containerization tools (e.g. Docker) package applications and their dependencies into containers for consistency across different 
       Environments.
  
  4. Deploy the Application on Server: like TOmcat


## Challenges in Manual Deployment:
   
   1. Every Day we need to deploy latest code.
   2. Deploy code in multiple environmentss.
   3. Takes a lot of time
   4. Repeated Work.
   Error Prone.
-----------------------------------------------------------------------------------------

# Jenkins :

 - Jenkins is a free and open source software.
 - Jenkins developedn using java language. ( to run jenkins we need java)
 - Jenkins is used to automate build and deployment process.
 - We can implement CI-CD using jenkins.

## What is CI-CD?

#### CI - Continous integration
#### CD - Continous Deployment/Delivery --> Delivery means app is ready for deployment  --> Deployment means deployment with approval

##### <> CI CD is one of the trending approach in software development life cycle.
##### <> CI CD is used to simplify and automate project deployment & Delivery process.

##### CI -> When code changes happen it should be ready to test
##### C Delivery -> Keep it ready to realese
##### C Deployment -> Deploy the project to production

### Note: For Production Deployment we need to take client approval
