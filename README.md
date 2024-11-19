# Workshop step-by-step instructions

# Step 1: create the eSignature template

## Step 1A: Log in to the developer account

* Open [https://account-d.docusign.com/](https://account-d.docusign.com/) and log in to your Docusign Developer account with the credentials that were assigned to you.

## Step 1B: Use the JSON file to create a new eSignature template

* Once logged in to the account, select **Templates** from the top-level menu.  
* Select the **Start** menu at the top-left and open it.  
* Under **Envelope Templates,** select **Upload Template**.  
* In the file picker, select the [JSON file provided to you for the eSignature template](https://github.com/docusign/discover-apis-workshop/blob/main/AccountOpeningWireTransferApproval.json).  
* Select **Open**.  
* You should see the new template in the list.

# Step 2: Create the web form

## Step 2A: Upload the web form configuration to create the web form

* Open [https://account-d.docusign.com/](https://account-d.docusign.com/) and log in to your Docusign Developer account.  
* Once logged in to the account, select **Templates** from the top-level menu.   
* Open the **Start** menu at the top left.  
* Under **Web Forms,** select **Upload Web Form**.  
* In the file picker, select the [JSON file provided to you for the Web Form](https://github.com/docusign/discover-apis-workshop/blob/main/Account_Opening_Template.json).  
* A **Web form template copy created** pop-up dialog will show; dismiss it.

## Step 2B: Activate and publish the new web form

* Select **Activate** at the top right of the screen.  
* A pop-up dialog will appear with **Public** already selected; select **Activate**.  
* A **Web Forms successfully activated\!** pop-up will show; dismiss it. 

# Step 3: Create the Maestro workflow

## Step 3A: Create a new workflow and decide how it will be triggered

* Open [https://account-d.docusign.com/](https://account-d.docusign.com/) and log in to the Docusign Developer account.  
* Once logged in to the account, select **Agreements** from the top-level menu.  
* Select **Maestro Workflows** from the left menu.  
* Select **Create Workflow** from the top-right.  
* From the pop-up dialog, select **Create Workflow**.  
* Select **Add workflow start** at the middle of the screen.  
* From the dropdown menu, select **From an API Call**.  
* Select **Next**.  
* Select **Next** (a second time).  
* Select **Apply**.

## Step 3B: Add the Web Form step and configure it

* Select **Add a step**.  
* Select **Collect Data with Web Forms** from the list.
* Select **Configure**.  
* From the **Choose form** dropdown menu, select **Account Opening**.  
* Select **Next**.  
* Select the **Select a participant** dropdown.  
* Select **Add Participants**.  
* In the pop-up dialog, select **Add Another Participant**.  
* Under **Participant 1,** give your participant a name (e.g., “Customer”).  
* Select **Save**.  
* Open the **Select a participant** dropdown menu and select the participant you created.  
* Select **Apply**.

## Step 3C: Add the Identity Verification step and configure it

* Select **\+** to add a new step.  
* Select **Verify Someone’s Identity** from the list**.**  
* Select **Configure**.  
* Select the **Select a participant** dropdown menu and select the participant you created.  
* Select **Next**.  
* Select the **Select identification verification** dropdown menu.  
* Select **DocuSign ID Verification** from the list.  
* Select **Next**.  
* Select the **Select variable to map to “Customer Name”** dropdown menu.  
* Select **Collect Data with Web Forms**.  
* Select **Customer Name**.  
* Select **Apply**.

## Step 3D: Add the eSignature step and configure it

* Select **\+** to add a new step.  
* Select **Get Signatures** from the list.  
* Select **Configure**.  
* Select the **Choose a template** dropdown menu.  
* Select **Account Opening Wire Transfer Approval** from the list.  
* Select **Next**.  
* Select the **Select a participant** dropdown menu and select the participant you created.  
* Select the **Name** dropdown menu, select **Collect Data with Web Forms,** and then **Customer Name**.  
* Select the **Email** dropdown menu, select **Collect Data with Web Forms,** and then **Customer Email**.  
* Select **Next**.  
* Select **Continue to map data fields (Optional)**.  
* Select the “Choose template” role and select **Applicant.**  
* For each of the following dropdowns: Name, Address1, Address2, City, State, and ZIP Code:  
  select **Collect Data with Web Forms** and then the matching property (leave the Amount, Source, Routing, and AccountType fields blank).  
* Select **Apply**.

## Step 3E: Install the Google extension app

* Open [https://apps-d.docusign.com/app-center](https://apps-d.docusign.com/app-center)   
* Select **Log In** at the top right.  
* If prompted, use the same Developer Account credentials you used before.  
* Find the **Google Drive** app tile and select it.  
* Select **Install App**.  
* Select **Continue**.  
* Once the app is installed, select **Connect Account**.  
* Log in with your Google credentials or select one from the list.  
* Select **Continue**.  
* Select **Continue**.  
* Dismiss the pop-up dialog if one shows up.

## Step 3F: Add the Google Archive step

* Select **\+** to add a new step.  
* Select **Store files in Google Drive** from the list.  
* Select **Configure**.  
* In the **Files to archive** dropdown menu, select **Get Siganture.combinedDocumentBaset64**.  
* Select **Next**.  
* In the **Select drive** dropdown menu, select **My Drive**.  
* Select **Add Folder**.  
* In the **Select Folder** dropdown menu, pick the folder you want to use.  
* Select **Next**.  
* In the **What will you call it** section, select **Add Variable**.  
* Select **Collect Data with Web Forms** and then select **Customer Name**.  
* Select **Apply**.

## Step 3G: Add a branching step

* Select **\+** to add a new step.  
* Select **Add a Branching Rule** from the list.  
* Select **Configure**.  
* From the **What will the rule check** dropdown menu, select **Collect Data with Web Forms** and then pick **Account Type (Selected Label)**.  
* From the **What operator will the rule use** dropdown menu, select **Equal to**.  
* In the **What result will the rule look for** textbox, type "Checking Account”.  
* Select the **Done** button.  
* Select the **Apply** button.

## Step 3H: Add confirmation screen steps

* Select the left **\+** button **(True)** to add a new step.  
* Select **Show a Confirmation Screen** from the list.  
* Select **Configure**.  
* Select the **Participant who will see messages** dropdown menu and then select the participant you created.  
* In the **Message title** and **Message body** textboxes both, write “Thank you for opening a new checking account.”  
* Select **Apply**.  
* Select the right **\+** button **(False)** to add a new step.  
* Select **Show a Confirmation Screen** from the list.  
* Select **Configure**.  
* Select the **Participant who will see messages** dropdown menu and then select the participant you created.  
* In the **Message title** and **Message body** textboxes both, write “Thank you for opening a new savings account.”  
* Select **Apply**.

## Step 3I: Publish the new workflow

* Select **Review & Publish** from the top right.  
* If everything is configured correctly, you should see **This workflow is ready to publish**.  
* Select **Publish**.  
* In the pop-up dialog, select **Authorize My Account**.  
* In the pop-up dialog, select **Allow Access**.  
* Select **Publish.**  
* Select **Go to Workflows**.  
* After a few seconds, the new workflow status should change to **Published**.

# Step 4: Use the VS Code Docusign Copilot Extension to obtain an access token

## Step 4A: Install the VS Code Docusign Copilot Extension

* Open VS Code.  
* Select **Extensions** on the left menu.  
* Select the three dots icon at the top of the menu.  
* Select **Install from VSIX…**  which you unzipped from DocusignVisualStudioCodeExtension.ZIP
* Go to [https://github.com/docusign/discover-apis-workshop/blob/main/docusign-copilot-extension.vsix](https://github.com/docusign/discover-apis-workshop/blob/main/docusign-copilot-extension.vsix) to find the VSIX file and select the **Download raw file** button on the top right.   
* Copy the VSIX file from GitHub into your local drive and select that file.  
* Select **Install**.  
* If asked to do so, restart VS Code.

## Step 4B: Use Copilot to obtain an access token

* Find the Copilot button ![][image1] at the bottom right corner of the screen and select it.  
* Select **Github Copilot Chat** from the menu.  
* Type @docusign /getAccessToken and press Enter.  
* Select **Sign In**.  
* If a VS Code pop-up dialog appears, select **Open**.  
* A web browser will appear. If asked to log in to Docusign, use the developer credentials you planned to use for this workshop.  
* After you log in, you should be automatically redirected back to VS Code and a new pop-up dialog will appear.  
* Select **Open**.  
* Select **Continue on the path of generating an access token** in the Copilot chat window.  
* In the question “Does your application need to perform automated tasks with Docusign without user intervention?” answer **No**.  
* In the question “Can your application securely store sensitive information like client secrets or private keys?” answer “**Yes**.”  
* When presented with three options, select “**Option 1: generate an IK automatically using Copilot chat.**”  
* Provide a name for your IK (integration key): type “Discover Workshop” and press Enter.  
* Enter a redirectURI for your IK. For this workshop, we do not need any particular URI, so let’s type the example provided, [http://localhost:3000/callback](http://localhost:3000/callback), into the Copilot chat box and press Enter.  
* Select **Open Consent URI in browser**.  
* If a VS Code pop-up dialog appears, select **Open**.  
* A web browser will appear; select **Allow Access** to continue.  
* The browser will now redirect to [http://localhost:3000/callback](http://localhost:3000/callback) and will show an error message. Please ignore this and find the URL that the browser has opened. It will include a URL parameter called “code” with a long token. Copy this token.  
* Back in the VS Code Copilot chat window, paste the value you copied and press Enter.  
* If everything worked correctly, you should see “Here is your Access Token” in the chat box, followed by the token (very long string).  
* Copy-paste the token and store it somewhere on your laptop. You’ll need it in the next step.

# Step 5: Use Maestro API to retrieve the trigger URL

## Step 5A: Import the Postman collection for this workshop

* Open a browser window and navigate to [www.postman.com](http://www.postman.com).  
* Select **Sign In** at the top.  
* Use your Postman credentials to log in to Postman.  
* Select **Workspaces** at the top left and then **Create Workspace**.  
* Select Next  
* In the Name textbox, type “Docusign Discover” and select **Create**.  
* Select **Import** at the top.  
* Select **files** in the middle.  
* Find the [Postman collection JSON file provided for this workshop](https://github.com/docusign/discover-apis-workshop/blob/main/Docusign%20Discover%20Workshop.postman_collection.json).  
* Select **Open**.  
* You should now see **Docusign Discover Workshop** and three GET requests on the left side.

## Step 5B: Call the Get Workflows Definitions endpoint using Postman

* Select the **Authorization** tab in the **Docusign Discover Workshop** Postman collection.  
* Paste the token from Step 4 into the **Token** textbox and then select **Save**.  
* Select the **Get Workflow Definitions** GET request from the list of API requests.  
* Replace the {{accountId}} placeholder with the account ID of your developer account.  
* Select **Send** to make the API call.  
* You should get back a JSON object starting with a count value that tells you how many workflows were found.  
* Find the workflow you created in Step 3 and copy the id property that you’ll need in the next step.

## Step 5C: Call the Get Workflows Definition endpoint using Postman

* Select the **Get Workflow Definition** GET request from the list of API requests.  
* Replace the {{accountId}} placeholder with the account ID of your developer account.  
* Replace the {{workflowId}} placeholder with the ID value of the workflow from the previous step.  
* Select **Send** to make the API call.  
* You should get back a JSON workflow definition for the specific workflow you created in step 3\.  
* The JSON object should include a value called triggerUrl. This is the endpoint of the API call you’ll use to trigger the workflow. Copy this value for use in the next step.

## Step 5D: Call the endpoint to trigger the workflow using Postman

* Select **\+** to add a new blank request.  
* Paste the triggerUl from the previous step into the **Enter URL or paste text** textbox.  
* In the action dropdown menu on the left, change the action from GET to POST.  
* Select **Headers**.  
* Select and delete “Key” and type “Authorization”.  
* In the Value textbox, type “Bearer ” and then paste the access token you saved from Step 4\.  
* Select **Body**.  
* Select the **raw** radio button.  
* Paste the following JSON into the textbox: ```{"instance_name": "Discover test run 1"}```
* Select **Send** to make the API call.  
* If everything was set up correctly, you should get back a small JSON object that includes an instanceId and a workflowInstanceUrl property.  
* Copy the workflowInstanceUrl property for use in the next step.

# Step 6: Use the URL from Step 5D to run through the workflow all the way to the end

## Step 6A: Fill out the web form

* Open a new web browser to the address you copied from the workflowInstanceUrl property at the end of the previous step.  
* Select **Start**.  
* Fill out all the details of the web form. Note: The Customer Name should match the name you’ll later use for identity verification.  
* Select **Next**.  
* Select **Submit**.

## Step 6B: Complete the Identity Verification process

* You should now see **Let’s verify your identity** on the top of the page.  
* Select **Next**.  
* On the next screen, select either **Driver’s license** or **Passport** for verification.  
* Select **I Agree**.  
* Option 1: Use your phone to scan images of your ID.  
* Option 2: Upload files showing the back and front of your ID.  
* Complete the identity verification process (should take 1–2 minutes).  
* You should see “Your identity was verified” and be redirected to the next step.

## Step 6C: Sign the envelope

* Select the **I agree to use electronic records and signature** checkbox.  
* Select **Continue**.  
* You should note that some of the data in the envelope was prefilled from the form you filled.  
* Fill in the rest of the data on the form (Feel free to use random/mock information).  
* Select **Sign** to sign the envelope.  
* Adopt a signature.  
* Select **Finish** at the top right.  
* You should now be redirected to the final confirmation page.

# Step 7: Use Navigator API to get a list of agreements

* Go back to your Postman collection window.  
* Select the **List Agreements** GET request from the list of API requests.  
* Replace the {{accountId}} placeholder with the account ID of your developer account.  
* Select **Send** to make the API call.  
* You should get back a JSON object with Agreement data from the Navigator product that should show the latest **Wire Transfer Agreement** that you signed in Step 6C.

# Appendix A \- list of files in the GitHub repository

1. This list of instructions (README).  
2. JSON file for eSignature Template definition (AccountOpeningWireTransferApproval.json).  
3. JSON file for Web Form configuration (Account\_Opening\_Template.json).  
4. Postman collection file (Docusign Discover Workshop.postman\_collection.json).  
5. ZIP file for VS Code extension (DocusignVisualStudioCodeExtension.zip). 

[image1]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABcAAAARCAYAAAA2cze9AAABlUlEQVR4XtWTIY/CMBzF+Rj4KjwY1BXBcgkGggAzDAmChJxHHKoYZkZIavYFNlFMBVlC0kzU7Du9a8fGLQx2d1xOnHhJ+2//v7Svr41ms4m/UuO2UBZpUzivjlEXrazWQjebO6BtUtl/q/twMgKLFNI0/ZSSkKo0N1IRw4jc6a+DO55EqiV2M4qOaSb9DYQ2QC2w6ZsTkw7obAdpatJzKv218HVkQNG6VJuAn03tzDGp3fcM/IVBZlZIsJeafd+BTw7Wb4XQ22Cz5RD21IXnZwG+NXUvhLK+HyaV/odwMmQQifVXQSUa2kgdOVbGa9JfgR9VVtOJWbfvkAiw4f3k3MAH8E95Gq7XNfHrdUCyMUGnV8Qyt8XuPfkYfA1fIyyiVsCn3Fw/hj8247GP2NjFpzfwNMT6eXgOLI9/Didw9/H1qq79hcTB/G0Omq3TbOzY7Lfdq4Xx3s1tq4VfRJcc0j6qTYMUCGxq3nN5AYTMf28iwZe00l8Lv6iFwYIhOMbQNhWFXVojPgZgi8H1YR+pBv57/V/4B199vDbs33fsAAAAAElFTkSuQmCC>
