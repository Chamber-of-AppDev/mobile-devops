# Manual resource setup guide
This guide provides step-by-step instructions to manually provision and configure the resources needed for the mobile-devops demo as well as instructions on how to run the demo.

Contents:
- [Manual resource setup guide](https://github.com/danelbernau/mobile-devops/edit/main/README.md#manual-resource-setup-guide)
  - [Step 1: Create a Visual Studio App Center app](https://github.com/danelbernau/mobile-devops/new/main?readme=1#step-1-create-a-visual-studio-app-center-app)
  - [Step 2: Set up your device sets](https://github.com/danelbernau/mobile-devops/new/main?readme=1#step-2-set-up-your-device-sets)
  - [Step 3: Generate API token](https://github.com/danelbernau/mobile-devops/new/main?readme=1#step-3-generate-api-token)
  - [Step 4: GitHub configuration](https://github.com/danelbernau/mobile-devops/new/main?readme=1#step-4-github-configuration)
  - [Step 5: Configure secrets](https://github.com/danelbernau/mobile-devops/edit/main/README.md#step-5-configure-secrets)
  - [Step 6: Configure actions](https://github.com/danelbernau/mobile-devops/edit/main/README.md#step-6-configure-actions)
  - [Step 7: Build, Test & Deploy](https://github.com/danelbernau/mobile-devops/edit/main/README.md#step-7-run-workflow)
  - [Troubleshooting](https://github.com/danelbernau/mobile-devops/edit/main/README.md#troubleshooting)


## Step 1: Create a Visual Studio App Center app
In this step, you create a Visual Studio App Center account and add a new app.
1. In the [Visual Studio App Center portal](https://appcenter.ms), sign in or register.
2. From the home page, select **Add new** > **Add new app** ![image](https://user-images.githubusercontent.com/107197611/174562762-940b61f8-9c6b-4a36-af49-081ba03a5c88.png)
3. Fill in the app name and select the OS & Platform. Choose **Android** as the OS and **Xamarin** as the platform. ![image](https://user-images.githubusercontent.com/107197611/174565930-aedd09b6-042d-4f0f-a85a-7c8ef9b1c2b1.png)
4. Repeat step 3 but with **Windows** as OS and **UWP** as the platform.

## Step 2: Set up your device sets
1. Navigate to the Android app created in [Step 3: Generate API token](https://github.com/danelbernau/mobile-devops/new/main?readme=1#step-3-generate-api-token). On the left-hand menu, select **Test** > **Device sets** > **New device set** ![image](https://user-images.githubusercontent.com/107197611/174572054-de4ce927-ccea-4b33-9324-2ccfdd5c2c12.png)
2. Fill in the device set name and select the devices you want to include in your device set. ![image](https://user-images.githubusercontent.com/107197611/174574721-7b9283f8-27a5-4795-a379-9acb626f01cf.png)

> All devices in this device set will form part of the tests performed as part of GitHub actions, the more devices included in the device set the longer the testing phase will take.

## Step 3: Generate API token
1. In the [Visual Studio App Center portal](https://appcenter.ms), click on your profile in the top right and select **Account Settings** ![image](https://user-images.githubusercontent.com/107197611/174582205-72b65b51-c82e-4f83-b4dc-9c167401a4d1.png)
2. Click on the icon in the **User API tokens** menu item ![image](https://user-images.githubusercontent.com/107197611/174582698-603b4a84-f81c-4225-bccc-f150e1c857ef.png)
3. Fill in the description and click on **Add new API token**. ![image](https://user-images.githubusercontent.com/107197611/174582984-815952eb-a4b8-4d50-88c5-effdcd2bdff2.png)
4. Make a note of the API token, this will be needed in [Step 5: Configure secrets](https://github.com/danelbernau/mobile-devops/edit/main/README.md#step-5-configure-secrets).

## Step 4: GitHub configuration
1. Create a new Fork from the [main GitHub repository](https://github.com/Chamber-of-AppDev/mobile-devops) ![image](https://user-images.githubusercontent.com/107197611/174584314-a71840ec-0db0-41eb-b1cc-4169f5a3c809.png)

> All GitHub configurations in steps 5 - 7 will be done on this fork.

## Step 5: Configure secrets

## Step 6: Configure actions

## Step 7: Run workflow

## Troubleshooting
