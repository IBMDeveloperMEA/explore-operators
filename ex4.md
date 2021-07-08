## Exercise 4 - Deploy new application back-end
We are now ready to deploy our back-end database application. This database is used to store patient data in the Health Care application. We will use the OpenShift CLI to deploy the application.
1.	Using Terminal #1, set project to example-health.
```
oc project example-health
```
Sample output:
```
Now using project "example-health" on server "https://c106-e.us-south.containers.cloud.ibm.com:30174".
```
2.	Using the S2I method, deploy the back end node.js application.
```
oc new-app --name=patient-db centos/nodejs-10-centos7~https://github.com/IBM/ibm-dte-openlab-samples --context-dir="/Red Hat OpenShift on IBM Cloud/nodejs-patientdb-cloudant-master" 
```
After a few minutes, the application is built, however, because we haven't specified our Cloudant DB credentials, the application repeatedly fails to start. Fix this using the OpenShift web console in the next steps.
3.	Navigate to the Topology page in the Developer perspective of the OpenShift web console.
If your page doesn't look like the picture below, make sure your Topology view has the project set to "example-health" and application filter set to all applications.
<br>![image](https://user-images.githubusercontent.com/36239840/124463728-5b3c8500-dda4-11eb-99c0-c32187830ec5.png)<br>
4.	Navigate to the Resources tab of the patient-db application.
Once the application is deployed (this might take a minute), notice the pod gets in a "CrashLoop BackOff" state. The deployment is failing because the application requires several environment variable to be set for the binding that you created to the Cloudant database.
<br>![image](https://user-images.githubusercontent.com/36239840/124463766-67c0dd80-dda4-11eb-954f-f3fcada877a0.png)
5.	Navigate to the deployment for the patient-db application.
<br>![image](https://user-images.githubusercontent.com/36239840/124463811-760ef980-dda4-11eb-816a-6202740c1e31.png)<br>
6.	Navigate to the Environment tab of the patient-db application and click Add from Config Map or Secret under the Single values (env) section.
<br>![image](https://user-images.githubusercontent.com/36239840/124463843-81fabb80-dda4-11eb-83d5-73fbb4ee3bbd.png)<br>
7.	Enter ```CLOUDANT_URL``` as the environment variable name, select ```cloudant-binding``` as the resource and url for the key.
```
CLOUDANT_URL
```
```
url
```
If you do not see the cloudant-binding in the resource pulldown, you most likely created the operator service and binding in the default project instead of the example-health project. If this is the case, you need to delete the existing binding and service in the IBM Cloud operator and recreate them using the example-health project. Refer to back to Exercise 3 for directions.
<br>![image](https://user-images.githubusercontent.com/36239840/124463946-a35ba780-dda4-11eb-877d-5a8792ca050a.png)<br>
8.	Click Save.
<br>![image](https://user-images.githubusercontent.com/36239840/124464050-c0907600-dda4-11eb-86fd-c6a59e0e58b1.png)<br>
9.	Verfiy the application has started without error.
<br>![image](https://user-images.githubusercontent.com/36239840/124464083-cbe3a180-dda4-11eb-95ae-c8134119b25f.png)<br>
It might take a few minutes for the build and deployment to complete. Wait until you see the green checkbox before proceeding to the next exercise.

## <a href="https://github.com/IBMDeveloperMEA/explore-operators/blob/master/ex5.md">Next Step: Exercise 5 - Configure Application to Use Cloudant</a>
