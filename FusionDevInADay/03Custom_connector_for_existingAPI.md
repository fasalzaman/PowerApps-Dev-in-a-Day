# Lab 03 - Custom connector for existing API

Duration: 140 mins

## Table of Contents

Lab Scenario 

1. Exercise 1 – Create Custom Connector 

    - Task 1: Download open API definition and create connector 

    - Task 2: Create custom connector 
   
    - Task 3: Modify the definition 

    - Task 4: Test connector 

2. Exercise 2 – Add Custom Code 

    - Task 1: Add code from resource folder 

    - Task 2: Test custom code 

3. Exercise 3 – Use Custom Connector 

    - Task 1: Test connector from canvas app

    - Task 2: Test connector from flow(This task is optional) 

### Lab Scenario

Working as part of the PrioritZ fusion team you will be configuring a custom connector for an existing
API. The team would like to add badging to the PrioritZ application to give credit to users when they
have completed ranking an item. The team identified an existing API, but it doesn't have a Power
Platform connector.

When you review the API, you see that it has four operations and uses API key authentication.


 ![](/images/L03/image1.png)

## Exercise 1 – Create Custom Connector

In this exercise, you will download open API definition, create a solution for Contoso Badges custom 
connector. Currently, custom connectors must be in a separate solution from the apps and flows that 
use them, and then create the custom connector.


### Task 1: Download open API definition and create connector

1. Navigate to the below URL to open the Contoso Coffee Badges API.

   ```
   https://contosobadgestest.azurewebsites.net/
   ```
2. Click on open the **Open API definition file** link.
   
    ![](/images/L03/image3.png)

3. Do a quick review of the Open API definition.

4. Right click on the page and select **Save as** and name the file as **swagger.json** in your machine. Now, close the browser tab by clicking on **X**.
      
     ![](/images/L03/image4.png)

### Task 2: Create custom connector

1. Navigate to Power Apps  maker portal and make sure you are in your dev environment named **DEV_ENV_<inject key="Deployment ID" enableCopy="false" />**.

         https://make.powerapps.com

2. Select **Solutions** and click **+ New solution**.

    ![](/images/L03/L03-solution.png)

3. Enter **Contoso Badges connector (1)** for Display name, select **Contoso Coffee (2)** for Publisher, and
    click **Create (3)**.
   
   ![](/images/L03/image2-1.png)
   
4. open the **Contoso Badges connector** solution you created.

5. Click **+ New (1) | Automation (2)** and select **Custom connector (3)**.
     
     ![](/images/L03/image5-1.png)

6. Enter the following information on the **Create Connector** blade.

     1. Connector name: **Badges connector (1)** 
     2. Description : **Connector for badges (2)**
     3. Host: **contosobadgestest.azurewebsites.net (3)** and 
     4. click **Create connector (4)**.
    
    ![](/images/L03/L03-badges1.png)

7. Select **Custom connectors (1)** from the sitemap.Click on the **... More actions (2)** button of the custom connector you created and select **Update from Open API file (3)** 

      ![](/images/L03/L03-custom.png)

8. Click **Import** to select the API file.

      ![](/images/L03/L03-import.png)

9. Select the **swagger.json** file you saved to your machine and click **Open**.

10. Click **Continue** on the **Import an OpenAPI file** pop-up.
    
    ![](/images/L03/image8-1.png)

11. Enter **Connector for badges (1)** for Description, **contosobadgestest.azurewebsites.net (2)** for Host,
    and advance to **Security (3)**.
      
      ![](/images/L03/image9-1.png)

12. Review the **security configuration (1)** and advance to **Definition (2)**.

      ![](/images/L03/L03-security.png)

13. Do not navigate away from this page.

### Task 3: Modify the definition

1. Select the **AddCredit (1)** action then **Important (2)** for Visibility.
    
     ![](/images/L03/image10-1.png)

2. Scroll down to the **Request** section, click on the chevron button of the **body** and select **Edit**.
     
     ![](/images/L03/image11.png)

3. Scroll down and Click on the chevron button of **points** and select **Edit**.
    
    ![](/images/L03/image12.png)

4. Select **Yes** for Is required and click on the **Back** button.
     
     ![](/images/L03/image13.png)

5. Click on the chevron button of **recipientid** and select **Edit**.

     ![](/images/L03/L03-recepient.png)

6. Select **Yes** for Is required and click on the  **Back** button.

     ![](/images/L03/image13.png)

7. Click on the chevron button of **name** and select **Edit**.

     ![](/images/L03/L03-name.png)

8. Select **Yes** for Is required and click on the  **Back** button.

     ![](/images/L03/image13.png)

9. Click on the **Back** button again.

      ![](/images/L03/image14.png)

10. Advance to **Code**.

11. Review the code and advance to **Test**.

      ![](/images/L03/L03-test.png)

12. Click **Update connector** and wait for the connector to be updated

     ![](/images/L03/image15.png)

13. Do not navigate away from this page.

### Task 4: Test connector

1. Open a new browser tab or window and navigate to the below URL to open Contoso Coffee Badges API. 
    ```
    https://contosobadgestest.azurewebsites.net/
    ```

2. Click on open the **API Key** link
    
   ![](/images/L03/image16.png)

3. Copy the **API Key** value and save it to notepad as you will be using this value in next steps. Now, close the browser tab by clicking on **X**.

4. Go back to the connector test page and click **+ New Connection**.
    
     ![](/images/L03/image17.png)

5. Paste the **API Key (1)** you copied in **step 3** of this task and click **Create connection (2)**.
   
    ![](/images/L03/image18-1.png)

6. Click on the **Refresh** connections button.
   
    ![](/images/L03/image19.png)


7. The connection you created should get selected.

8. Go to the **AddCredit (1)** operation. Enter your email address for **recipientid**, enter your name for **name**, enter **1** for points, and click
    **Test operation (2)**.
    
    ![](/images/L03/image20-1.png)

9. The test should succeed, and the response should look like the image below.
     
     ![](/images/L03/image21.png)


## Exercise 2 – Add Custom Code

In this exercise, you will add a new operation to only return the current badge name and image URL.
You will do this by using the custom code feature to reshape the response from the API.

>**Note**: If you already have the custom connector open, skip to **step 4**

### Task 1: Add code from resource folder

1. Navigate to Power Automate using below URL.
          
   ```
   https://make.powerautomate.com
   ```

2. Expand **Data (1)** and select **Custom connectors (2)**.

     ![](/images/L03/L03-connector.png)

3. Click the **Edit** button of the custom connector you created.

    ![](/images/L03/image24.png)

4. Select the **Definition** tab from the dropdown and click **New action** in the definition tab.
  
    ![](/images/L03/L03-EX3.1.png)

5. Enter the following information to add **Get current badge** action.

     1. Summary: **Get current badge**
     2. Description: **Get current badge (2)** 
     3. Operation ID: **getcurrentbadge (3)**
    
    
    ![](/images/L03/image26-1.png)

6. Scroll down to the **Request** section and click **+ Import from sample**.
    
    ![](/images/L03/image27.png)

7. Select **Get (1)** for Verb, enter the below value for **URL (2)**, and click **Import (3)**.
   ```
   https://contosobadgestest.azurewebsites.net/getcurrentbadge?id={id} 
   ```

    ![](/images/L03/image28-1.png)

8. Click **Update connector** and wait for the connector to be updated.

9. Select the **Code** tab.

10. Enable **Code (1)** and click **Upload (2)**.
    
     ![](/images/L03/image29-1.png)

11. Select the **CustomConnectorCode.csx** file located in this path `C:\LabFiles\Developer-in-a-day\Student\L03 - Custom connector for existing API\Resources` and click **Open**.

12. Select the **getcurrentbadge** action from the dropdown.
     
     ![](/images/L03/image30.png)

13. Review the code you just added.

14. Click **Update connector** and wait for the connector to be updated.

15. Advance to **Test** by selecting it in the dropdown.

16. Select the **getcurrentbadge** action.

17. Provide your email address as id and click **Test operation**.
     
     ![](/images/L03/image31-1.png)

18. The test should succeed, and you should get current badge for the user you created.
    
    ![](/images/L03/image32.png)
    
    > **Note**: If the test operation fails, try updating the connector then test the connector by performing Steps 15-18 again.

19. Copy the Response **Body** JSON.

20. Select the Definition tab from the dropdown.

21. Select the **getcurrentbadge** action.
     
      ![](/images/L03/image33.png)

22. Scroll down to the **Response** section and click **+ Add default response.**
 
      ![](/images/L03/image34.png)


23. Paste the JSON you copied in the **Body (1)** and click **Import (2)**.
     
     ![](/images/L03/image35-1.png)

24. Click **Update connector** and wait for the connector to be updated.

25. **Do not** navigate away from this page.

### Task 2: Test custom code

In this task, you will test your custom code.

1. Select the **Test** tab.

2. Select the connection you created earlier.

3. Go to the **Operations** section and select the **getcurrentbadge (1)** operation. Provide your email as **id (2)** and click **Test operation (3)**.
   
     ![](/images/L03/image36-1.png)

4. The operation should succeed, and the response **Body** should look like the image below.
    
    ![](/images/L03/image37.png)

## Exercise 3 – Use Custom Connector

In this exercise, you will test the custom connector you created using a flow and a canvas application.

### Task 1: Test connector from canvas app

In this task, you will use the custom connector you created to show the user’s current badge on the PrioritZ Ask canvas application.

1. Navigate to **Power Apps** maker portal using the below URL if not already open and make sure you are in your dev environment.
   ```
   https://make.powerapps.com
   ```

2. Expand **Solutions** and open the **PrioritZ** solution.

3. Select **Apps (1)** , select the **PrioritZ Ask (2)** application, and click **Edit (3)**.
 
     ![](/images/L03/image38-1.png)

4. Select **Data** from the left and click **+ Add data.**
     
     ![](/images/L03/image39.png)

5. Expand **Connectors** and select the **Badges connector** you created.
    
    ![](/images/L03/image40.png)


6. Click **+ Add a connection**.

    ![](/images/L03/L03-EX4.png)

7. Open a new browser tab or window and navigate to the below URL to open the Contoso Coffee Badge API.
    
    ```
    https://contosobadgestest.azurewebsites.net/
 
    ```
    
8. Click on the **open the API Key** link
     
    ![](/images/L03/image41.png)

9. Copy the **API Key** value and paste the value to notepad as you will be using this value in next steps. Now, close the browser tab by clicking on **X**.

10. Go back to the app designer, paste the **API Key (1)** you copied in the previous step, and click **Connect (2)**.
     
     ![](/images/L03/image42-1.png)


11. Select the **Tree view**.

12. Select the **Components (1)** tab, Click ** + Insert (2)** tab, search for image and then select **Image (2)**.
     
     ![](images/L03/image.png)

13. Double click on the newly added image and change it's name to **User badge**.
    
     ![](/images/L03/image44.png)


14. Set the User badge **Image** value to the formula below.

    ```
    ContosoBadges.getcurrentbadge({id:User().Email}).image
    ```
    ![](/images/L03/image45.png)

15. Set the Tooltip value of the User badge to the formula below.

    ```
    ContosoBadges.getcurrentbadge({id:User().Email}).name
    ```
    ![](/images/L03/L03-EX4-T1.png)

16. Make the image smaller and move it to top right corner of the screen.

17. The User badge should now look like the image below.
      
     ![](/images/L03/image46.png)

18. Select **Screens** tab in the Tree view. Click **Play** button.

19. Hover over the badge to see the badge name.
      
      ![](/images/L03/image47.png)

20. Close the preview.

21. Select **Publish**.

22. Select **Publish this version**.

23. Go back to the solution by clicking on the  **Back** button.
     
      ![](/images/L03/imagee47.png)

25. Do not navigate away from this page.

### Task 2: Test connector from flow(This task is optional)

1. Make sure you are still in the **PrioritZ** solution.

2. Click **+ New** and select **Automation | Cloud flow | Instant**.

    ![](/images/L03/image48.png)

3. Enter **Test add credit** for flow name, select **Manually trigger a flow** , and click **Create**.
     
    ![](/images/L03/edd%20(1).png)

4. Click **+ New step**.

    ![](/images/L03/L03-EX3-T2.png)

5. Select the **Custom** tab and then select the **Add credit** action.
   
    ![](/images/L03/edd%20(2).png)
    
6. Enter **Test connection** , paste the **API Key** you copied earlier in **step 9** of task1 in this exercise, and click **Create**.
  
    ![](/images/L03/edd%20(3).png)

7. Click on the **recipientId** field, go to the Dynamic content pane, and select **User email**.
    
     ![](/images/L03/image49.png)

8. Click on the **name** field, go to the Dynamic content pane, and select **User name**.

9. Enter **1** for points and click **Save**. Wait for the flow to be saved.
   
     ![](/images/L03/image50.png)

10. Click **Test**.

     ![](/images/L03/L03-EX4-test.png)

11. Select **Manually** and click **Test** again.

     ![](/images/L03/L03-EX3-manually.png)

12. Click **Continue**.

13. Click **Run flow**.

14. Click **Done**.

15. The flow run should succeed. Once succeeded, click on the **Back** button.
    
     ![](/images/L03/image51.png)

17. Select **Cloud flows** and open the flow you created.
     
     ![](/images/L03/image52.png)

18. Start a new browser window and navigate to Power Apps maker portal.

19. Make sure you are the correct environment.

20. Select **Apps** and launch the **PrioritZ Ask** application.

21. The application should now show **First Badge**.
  
     ![](/images/L03/image53.png)

22. Go back to flow and run it couple more times.

     ![](/images/L03/L03-EX4-run1.png)

23. Go back to the **PrioritZ Ask** application and refresh the page.

24. You should now see the **Team Player** badge.
  
     ![](/images/L03/image54.png)

25. Go to the flow and run it two more times.

26. Go back to the **PrioritZ Ask** application and refresh the page.

27. You should now see the **Champ** badge
   
     ![](/images/L03/image55.png)
