# MetaAds Decentraland's Scene

## Introduction

In this document you can see instruction by adding MetaAds Typescript (Javascript + Types) files to your Decentraland's Scene.
The result will be displaying the image/video, which arrives from the backend service.
This scene is written with a Decentraland SDK -- a powerful tool, that give ability you to create scenes by writing in Typescript (TS).

## 1. Install the CLI

The Command Line Interface (CLI) allows you to compile and preview your scene locally.
After testing your scene locally, you can use the CLI to upload your content to Decentraland.

### 1.1 Base enviromnent

You should have [Node.js](https://nodejs.org/en/) (version 14 or later) and CLI that is installed globally:

```console
npm i -g decentraland
```

### 1.2 SDK Libraries

Next libs will be used:

+ *decentraland-ecs-utils* (for sending requests to server with some interval);
+ *decentraland-ecs* (for identifying of parcel coords, collecting of metrics from scene and sending signed requests).

Run the folowing commands in your CLI:

```console
npm i decentraland-ecs@latest
npm i @dcl/ecs-scene-utils -B
```

## 2. Preparing the scene

Choose from the cases, that possible:

1. You have already got a scene:
    + If it was created with [Builder](https://builder.decentraland.org/), you need download the scene and unzip downloaded archive. Example of scene creation is on the picture:
    ![Download a scene from Builder](./images/builder_download_scene.png)
    + If it was created with SDK, then move to the 3 step.
2. You don't have any scene at the moment. There is need to create it with SDK. To create scene, run: ```dcl init``` in CLI from empty dir and select *Scene*.

## 3. Adding MetaAds files

After downloading MetaAds scene's [files](https://metaads.team/app/ad-space), copy all files **except** of *game.ts* in **your** scene directory.
Open **MetaAds** *game.ts* file, copy code and paste it to **your** *game.ts*.

> Note: Please, check whether your and our imports of dependencies are not intersected.

## 4. Setup of displays

> Note: [Set up coords](https://docs.decentraland.org/development-guide/scene-metadata/#scene-parcels) of your parcel in file *scene.json* before testing and deploying.

There is a block of code in *game.ts*, which you should to customize for yourself. It consists sizes and positions your displays.
For start, find in code pointed block, it starts from *Change these parameters* and ends *End block*.
First parameter *n* is a number of displays that you are putting on the scene.
The next parameters are arrays:

+ *metaAdsScales* contains sizes of displays. Size is three-component variable. First and second numbers are width and height.
Third number is dummy variable and it always equals 1, because it is a thickness, but display is flat, so you shoudln't change it.
+ *metaAdsPositions* has the same dimension, but its three variables are x, y and z. The position of the display's center on all three axes.
+ *metaAdsImageRotations*. Euler angles, the more common x, y and z notation with numbers that go from 0 to 360.
The values are set up by default put a screen vertical. If you wish to tilt dislpay forward or backward, change first parameter.
If you should to rotate on left or right, change second value. And if want tilt to left or right, use third parameter.

> Note: Add to array the same objects that arrays already have, separeted with commas, changing their contains.

> Note: The number of objects in each of arrays should be equal to the number of displays *n*.

## 5. Health check

At the first, run the next command (for locally display of the scene):

```console
dcl start --web3
```

A window in a browser with your scene is opened automatically. Also, window with confirmation of your wallet is appeared.

> Note: Key *--web3* allows to use a wallet in local preview of scene.

![Preview of scene](./images/scene_preview.png)

## 6. Deploying

To publish the scene in Decentaland's world, write this command:

```console
dcl deploy
```

![Select parcel](./images/deploy_map.png)

After that should appeared new tab with button, which allows to deploy the scene.

> Note: Confirm deploying in appeared window from your wallet.

The link of your parcel is seen in CLI after deploying has been finished.

![Result](./images/parcel_in_publish_world.png)

That's all!
