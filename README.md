# Explore Operators and Simplify App Deployment
## Architecture Diagram
![image](https://user-images.githubusercontent.com/36239840/124466277-8bd1ee00-dda7-11eb-8aed-3e35394ca263.png)
![image](https://user-images.githubusercontent.com/36239840/124932347-0d2db880-e014-11eb-9627-b15778f99825.png)
![image](https://user-images.githubusercontent.com/36239840/124932424-1e76c500-e014-11eb-95aa-f864a44f93fc.png)

## Prerequisites
- Register to participate in the live stream or watch the replay: https://www.crowdcast.io/e/bsok-bootcamp/
- Create your free IBM Cloud account at https://ibm.biz/bsok-series
- Red Hat OpenShift Cluster
  - URL: https://bsokbootcamp.mybluemix.net/
  - Key: oslab
## Steps
- <a href="https://github.com/IBMDeveloperMEA/explore-operators/blob/master/README.md">Create Project & Deploy frontend app</a>
- <a href="https://github.com/IBMDeveloperMEA/explore-operators/blob/master/ex2.md">Install IBM Cloud Operator from Operator Hub</a>
- <a href="https://github.com/IBMDeveloperMEA/explore-operators/blob/master/ex3.md">Create a Cloudant service</a>
- <a href="https://github.com/IBMDeveloperMEA/explore-operators/blob/master/ex4.md">Deploy new application back-end</a>
- <a href="https://github.com/IBMDeveloperMEA/explore-operators/blob/master/ex5.md">Configure Application to Use Cloudant</a>
## Exercise 1 - Create Project & Deploy app
In this exercise, deploy a simple Node.js Express application - "Example Health". Example Health is a simple UI for a patient health records system. We will use this example to demonstrate key OpenShift features throughout this workshop.
Deploy Example Health
1.	Launch the OpenShift web console, if not already running.
You should still have a browser tab open with the OpenShift web console from the previous exercise. We will use the web console for this exercise. If you closed that tab, you can access your OpenShift web console on via ##OPENSHIFT.dashboardUrl##.
2.	Use the Developer perspective. If you are currently in the Administrator perspective, switch to the Developer perspective.
<br>![image](https://user-images.githubusercontent.com/36239840/124442946-4a811480-dd8e-11eb-9baa-69db958ab342.png)<br>
You may be prompted with a "Welcome to Dev Perspective!" tour dialog, if so, click the "Skip tour" button.
3.	While on the Topology page, click the create a project link.
<br> ![image](https://user-images.githubusercontent.com/36239840/124442970-5076f580-dd8e-11eb-8603-c6e6855aa53e.png)<br>

4.	Enter "example-health" as the new project's Name.
example-health
Optionally specify a Display Name and Description.
 <br>![image](https://user-images.githubusercontent.com/36239840/124443001-58cf3080-dd8e-11eb-970d-3323b69c9e52.png)<br>

5.	You should see a view that looks like this.
<br> ![image](https://user-images.githubusercontent.com/36239840/124443022-5d93e480-dd8e-11eb-964c-9054b957b410.png)<br>

6.	Let's deploy the application by selecting the From Git tile.
 <br>![image](https://user-images.githubusercontent.com/36239840/124443044-6389c580-dd8e-11eb-9590-c0fad9061057.png)<br>

7.	In the Git Repo URL field, enter: 
```
https://github.com/IBM/ibm-dte-openlab-samples
```

8.	Press the tab key to validate the repository path.
Note: If you receive an error regarding invalid repository, make sure you do not have any trailing spaces in the repo field. You can ignore the "Unable to detect the builder image" message, we will fix that in the next step.
9.	Click Show Advanced Git Options.
10.	Enter /Red Hat OpenShift on IBM Cloud/node-s2i-openshift-master/ in the Context Dir field.
```
Red Hat OpenShift on IBM Cloud/node-s2i-openshift-master/
```
Note: there is a leading "/" already in the entry field. If you copy from the lab guide, click in the field and do a paste or control v, the correct value will be: "/Red Hat OpenShift on IBM Cloud/node-s2i-openshift-master/".
<br> ![image](https://user-images.githubusercontent.com/36239840/124443070-6c7a9700-dd8e-11eb-93e3-ca7d3ea2ea33.png)<br>

11.	Scroll down and select the Node.js tile under Builder Image.
 <br>![image](https://user-images.githubusercontent.com/36239840/124443098-71d7e180-dd8e-11eb-87e7-74469144eceb.png)<br>

12.	Scroll down and change Application Name to ```patient-ui``` and Name to ```node-s-2-i-openshift```.
```
patient-ui
```
```
node-s-2-i-openshift
```
Note: These values are used later in this lab as well as Lab 2. If you change these names, remember the values and make appropriate changes in the subsequent steps.
<br> ![image](https://user-images.githubusercontent.com/36239840/124443119-77cdc280-dd8e-11eb-9bad-d57f32323342.png)<br>

13.	Click Create at the bottom of the window to build and deploy the application.
Your application is being deployed. This takes a few minutes. While it is being deployed, you see the state icon of your application change:
<br> ![image](https://user-images.githubusercontent.com/36239840/124443145-7bf9e000-dd8e-11eb-8f35-4f96e9d791e0.png)<br>

14.	Once the application has been completely deployed, the bottom icon changes to a green check mark.
Note: During the build process, OpenShift will register 2 or 3 image pull errors. The application should successfully deploy within a couple of minutes. If it does not, review the logs and events as described in subsequent exercises in this lab, or delete the application from your topology and deploy it again making sure to specify the information exactly as described in this lab guide.
<br> ![image](https://user-images.githubusercontent.com/36239840/124443194-874d0b80-dd8e-11eb-9b38-f0b6b6ca4659.png)<br>

15.	Click the Node.js label in the graphic. A panel like below is displayed.
<br> ![image](https://user-images.githubusercontent.com/36239840/124443212-8ae09280-dd8e-11eb-8ce2-6344ad1b64dc.png)<br>

This panel displays the details about your Pods, Builds, Services and Routes. Note that Build #1 should be complete. If it is not yet complete, wait until it changes to the complete state (green check mark) before continuing.
- Pods: the Node.js application containers
- Builds: auto-generated build of Docker image from your Node.js source 
- Services: access to pods and listening ports
- Routes: exposed service route using LoadBalancer provided by IBM Cloud network

### <a href="https://github.com/IBMDeveloperMEA/explore-operators/blob/master/ex2.md">Next Step: Exercise 2 - Install IBM Cloud Operator from Operator Hub</a>
