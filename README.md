# Manual resource setup guide
This guide provides step-by-step instructions to manually provision and configure the resources needed for the mobile-devops demo as well as instructions on how to run the demo.

Contents:
- [Manual resource setup guide](https://github.com/danelbernau/mobile-devops#manual-resource-setup-guide)
  - [Step 1: Create a Visual Studio App Center app](https://github.com/danelbernau/mobile-devops#step-1-create-a-visual-studio-app-center-app)
  - [Step 2: Set up your device sets](https://github.com/danelbernau/mobile-devops#step-2-set-up-your-device-sets)
  - [Step 3: Generate API token](https://github.com/danelbernau/mobile-devops#step-3-generate-api-token)
  - [Step 4: GitHub configuration](https://github.com/danelbernau/mobile-devops#step-4-github-configuration)
  - [Step 5: Configure secrets](https://github.com/danelbernau/mobile-devops#step-5-configure-secrets)
  - [Step 6: Configure actions](https://github.com/danelbernau/mobile-devops#step-6-configure-actions)
  - [Step 7: Build, Test & Deploy](https://github.com/danelbernau/mobile-devops#step-7-build-test--deploy)
  - [Troubleshooting](https://github.com/danelbernau/mobile-devops#troubleshooting)


## Step 1: Create a Visual Studio App Center app
In this step, you create a Visual Studio App Center account and add a new app.
1. In the [Visual Studio App Center portal](https://appcenter.ms), sign in or register.
2. From the home page, select **Add new** > **Add new app** ![image](https://user-images.githubusercontent.com/107197611/174608073-57381eda-707b-4815-8783-03fa9e4dcae0.png)

3. Fill in the app name and select the OS & Platform. Choose **Android** as the OS and **Xamarin** as the platform. ![image](https://user-images.githubusercontent.com/107197611/174608600-c5d80d7c-6d1e-4a42-b429-279cc53f8e47.png)

4. Repeat 2 & 3 but with **Windows** as OS and **UWP** as the platform.

## Step 2: Set up your device sets
1. Navigate to the Android app created in [Step 1: Create a Visual Studio App Center app](https://github.com/danelbernau/mobile-devops#step-1-create-a-visual-studio-app-center-app). On the left-hand menu, select **Test** > **Device sets** > **New device set** ![image](https://user-images.githubusercontent.com/107197611/174609023-a6fd3f38-7b17-4791-8291-e13a874fdbe9.png)
2. Fill in the device set name and select the devices you want to include in your device set. ![image](https://user-images.githubusercontent.com/107197611/174574721-7b9283f8-27a5-4795-a379-9acb626f01cf.png)

> All devices in this device set will form part of the tests performed during the build, test & deploy workflow in GitHub actions. The more devices included in the device set the longer the testing phase will take.

## Step 3: Generate API token
1. In the [Visual Studio App Center portal](https://appcenter.ms), click on your profile in the top right and select **Account Settings** ![image](https://user-images.githubusercontent.com/107197611/174582205-72b65b51-c82e-4f83-b4dc-9c167401a4d1.png)
2. Click on the icon in the **User API tokens** menu item ![image](https://user-images.githubusercontent.com/107197611/174582698-603b4a84-f81c-4225-bccc-f150e1c857ef.png)
3. Fill in the description and click on **Add new API token**. ![image](https://user-images.githubusercontent.com/107197611/174582984-815952eb-a4b8-4d50-88c5-effdcd2bdff2.png)
4. Make a note of the API token, this will be needed in [Step 5: Configure secrets](https://github.com/danelbernau/mobile-devops#step-5-configure-secrets).

## Step 4: GitHub configuration
1. Create a new Fork from the [main GitHub project](https://github.com/Chamber-of-AppDev/mobile-devops) ![image](https://user-images.githubusercontent.com/107197611/174584314-a71840ec-0db0-41eb-b1cc-4169f5a3c809.png)

> All GitHub configurations in steps 5 - 7 will be done on this fork.

## Step 5: Configure secrets
1. In the newly created fork from [Step 4: GitHub configuration](https://github.com/danelbernau/mobile-devops#step-4-github-configuration), go to **Settings** > **Secrets** > **Actions** > **New repository secret** ![image](https://user-images.githubusercontent.com/107197611/174593367-75643080-2b5d-432f-b1e2-a84ddd8ade4c.png)
2. Fill in the secret name and value and click on **Add secret** ![image](https://user-images.githubusercontent.com/107197611/174593645-ea273814-3039-4a44-9664-a41edfe81484.png)
3. Make sure all the secrets are added 
   - `ANDROID_SIGNING_KEY_ALIAS` android_keystore
   - `ANDROID_SIGNING_KEY_BASE64` [Android signing key base64](/src/Xamarin.Demo/self-signed-certs/android-keystore.keystore.b64)
   - `ANDROID_SIGNING_KEY_STORE_PASSWORD` 12341234
   - `APP_CENTER_API_TOKEN` token generated in [Step 3: Generate API token](https://github.com/danelbernau/mobile-devops#step-3-generate-api-token)
   - `UWP_CERTIFICATE_BASE64` [UWP certificate base64](/src/Xamarin.Demo/self-signed-certs/Xamarin.Demo.App.UWP_TemporaryKey.pfx.b64)
   - `UWP_CERTIFICATE_PASSWORD` 1234
   ![image](https://user-images.githubusercontent.com/107197611/174593943-8def5530-a282-4884-be24-2f2ded349b1c.png)

## Step 6: Configure actions
1. In the newly created fork from [Step 4: GitHub configuration](https://github.com/danelbernau/mobile-devops#step-4-github-configuration), go to the workflow file [..mobile-devops/.github/workflows/appcenter-cloud-device-test.yml](/.github/workflows/appcenter-cloud-device-test.yml)
2. Locate and update the following slugs
   - `appcenterAndroidAppSlug` [app-center-username]/[app-center-android-app-name]
   - `appcenterAndroidDeviceSetSlug` [app-center-username]/[app-center-android-device-set-name]
   - `appcenterUwpAppSlug` [app-center-username]/[app-center-windows-app-name]
 ![image](https://user-images.githubusercontent.com/107197611/174596479-c38d1e15-8989-4ba6-892c-b63c62f0d40d.png)


## Step 7: Build, test & deploy
1. In the newly created fork from [Step 4: GitHub configuration](https://github.com/danelbernau/mobile-devops#step-4-github-configuration), go to **Actions** and enable if prompted
2. Select the **Build & Test on AppCenter** workflow
3. Click on the **Run workflow** button ![image](https://user-images.githubusercontent.com/107197611/174613185-d8fa6ed0-16e2-4bea-9476-fbea17ceb71e.png)
4. You can check the progress of the workflow while it is running by selecting the active workflow. You can also select each specific job to check individual progress. ![image](https://user-images.githubusercontent.com/107197611/174613963-1d647619-82f5-4455-be68-5f967a69e356.png)
5. Once the build succeeds and testing on the devices start, you can check the progress in the [Visual Studio App Center portal](https://appcenter.ms) ![image](https://user-images.githubusercontent.com/107197611/174618932-bb4f2777-eabd-4570-add8-bbeeb932eb1c.png)
6. Once build, test & deployment succeeds all jobs will display as green ![image](https://user-images.githubusercontent.com/107197611/174614099-65420075-4f62-4785-9a4e-e93cf8a6413b.png)
7. Test history is available in the [Visual Studio App Center portal](https://appcenter.ms) as well ![image](https://user-images.githubusercontent.com/107197611/174619233-171369c0-0784-4912-9544-bcaf15daf571.png)


## Troubleshooting
- If you get a certificate error, update the secrets and make sure there are no leading / trailing white spaces when copying the name & value
- If you are using a free App Center account you will get an error related to device testing ![image](https://user-images.githubusercontent.com/107197611/174614772-d2033b8a-d94b-4905-9e80-48063186cb35.png) You can sign up for a 30-day free trial to enable device testing and re-run the workflow ![image](https://user-images.githubusercontent.com/107197611/174614856-a1eed06e-a8dc-42ca-a35a-8a1b56b0c2ad.png)


