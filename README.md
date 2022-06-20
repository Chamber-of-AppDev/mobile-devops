# Manual resource setup guide
This guide provides step-by-step instructions to manually provision and configure the resources needed to run the mobile-devops demo.

Contents:
- [Step 1: Create a Visual Studio App Center app](https://github.com/danelbernau/mobile-devops/new/main?readme=1#step-1-create-a-visual-studio-app-center-app)
- [Step 2: Set up your device sets](https://github.com/danelbernau/mobile-devops/new/main?readme=1#step-2-set-up-your-device-sets)
- [Step 3: Generate API token](https://github.com/danelbernau/mobile-devops/new/main?readme=1#step-3-generate-api-token)
- [Step 4: GitHub configuration](https://github.com/danelbernau/mobile-devops/new/main?readme=1#step-4-github-configuration)


## Step 1: Create a Visual Studio App Center app
In this step, you create a Visual Studio App Center account and add a new app.
1. In the [Visual Studio App Center portal](https://appcenter.ms![image](https://user-images.githubusercontent.com/107197611/174560552-1fdb96ca-156b-46bf-8baf-c61233fb80d6.png)
), sign in or register.
2. From the home page, select **Add new** > **Add new app** ![image](https://user-images.githubusercontent.com/107197611/174562762-940b61f8-9c6b-4a36-af49-081ba03a5c88.png)
3. Fill in the app name and select the OS & Platform. Choose **Android** as the OS and **Xamarin** as the platform. ![image](https://user-images.githubusercontent.com/107197611/174565930-aedd09b6-042d-4f0f-a85a-7c8ef9b1c2b1.png)
4. Repeat step 3 but with **Windows** as OS and **UWP** as the platform.

## Step 2: Set up your device sets
1. Navigate to he Android app created in Step 3. On the left-hand menu, select **Test** > **Device sets** > **New device set** ![image](https://user-images.githubusercontent.com/107197611/174572054-de4ce927-ccea-4b33-9324-2ccfdd5c2c12.png)
2. Fill in the device set name and select the devices you want to include in your device set. ![image](https://user-images.githubusercontent.com/107197611/174574721-7b9283f8-27a5-4795-a379-9acb626f01cf.png)

> All devices in this device set will form part of the tests performed as part of GitHub actions, the more devices included in the device set the longer the testing phase will take.

## Step 3: Generate API token

## Step 4: GitHub configuration
