# Bitcoin Factory Crowd-Testing of Machine Learning Models.

## Introduction

### What is this?

This Test Client App is to be used to crowd-test machine learning models with the goal of finding the best combination of parameters / data that produces the best possible forecasts.

### Why do we need this?

When working with Machine Learning models, soon you realize that even though they could work to make financial forecasts, you need to set a whole array of parameters that not only define the architecture of the model, but also the shape of the data and may other things. For each of these parameters, there is a valid range of values that could work, but only in combination with other parameters which also have their own valid ranges.

Nobody knows what combination is going to produce the best results for a particular Asset / Timeframe. Machine Learning models accuracy is determined by the error measured when producing forecasts using a test dataset after training the model. These forecasts are compared with the actual values and from there an objective Error measure is taken. 

In order to obtain that error measure, first a ML model with certain parameters and certain data need to be created and trained, which usually takes time (from a few minutes to potentially hours). 

Testing combinations of parameters and data (with potentially hundreds of indicators to choose from, thousands of crypto assets, and dozens of time-frames) by hand, one by one, would be a nightmare. The system from which this App is part of, solves those problems by automating the discovery of the best performing ML models, for a certain range of parameters values and certain set of indicators, for each combination of Asset / Timeframe. 

The System allows us to define for each parameter a range of valid values, creating a set of Test Cases based on all the possible combinations of all the values inside the valid  ranges for all parameters. Then we only need distributed processing power to test all the combinations in a reasonable time and find which parameters / data configurations produces the best results. Best results means the best forecasts with the lowest % of error.

Over time, we will learn we will learn which set of parameters and data produces the best model for a certain Asset / Timeframe. If we never stop testing, we will over time get the best possible models. Even if we finish with all possible combinations, datasets are changing over time and the amount of records and the data itself influence the performance of a ML model. For that reason, testing models is a never ending task. 

It is important to understand that this Test Client APP does not prepare the dataset to be tested. This is done by the Test Server App. That means that this app does not need to be ran together with Superalgos or any other data provider for the purpose of extracting data from it. It only depends on the Test Server which handles the management of the Test Cases and the generation of the datasets to be used at each one of the tests.

This App does need Superalgos to save the best predictions as indicators in there.

### Example of Parameters [Fraction of the actual list]

┌─────────────────────────────────────────────────────────────────────────┬─────────┬────────┐
│                                 (index)                                 │    0    │ Values │
├─────────────────────────────────────────────────────────────────────────┼─────────┼────────┤
│                             LIST_OF_ASSETS                              │  'BTC'  │        │
│                           LIST_OF_TIMEFRAMES                            │ '01-hs' │        │
│                     NUMBER_OF_INDICATORS_PROPERTIES                     │         │   7    │
│                         NUMBER_OF_LAG_TIMESTEPS                         │         │   5    │
│                            NUMBER_OF_ASSETS                             │         │   1    │
│                            NUMBER_OF_LABELS                             │         │   3    │
│                   PERCENTAGE_OF_DATASET_FOR_TRAINING                    │         │   80   │
│                           NUMBER_OF_FEATURES                            │         │   7    │
│                            NUMBER_OF_EPOCHS                             │         │  100   │
│                         NUMBER_OF_LSTM_NEURONS                          │         │   50   │
│               CANDLES_CANDLES-VOLUMES_CANDLES_CANDLE_MAX                │         │  'ON'  │
│               CANDLES_CANDLES-VOLUMES_CANDLES_CANDLE_MIN                │         │  'ON'  │
│              CANDLES_CANDLES-VOLUMES_CANDLES_CANDLE_CLOSE               │         │  'ON'  │
│                               HOUR_OF_DAY                               │         │ 'OFF'  │
│                              DAY_OF_MONTH                               │         │ 'OFF'  │
│                               DAY_OF_WEEK                               │         │ 'OFF'  │
│                              WEEK_OF_YEAR                               │         │ 'OFF'  │
│                              MONTH_OF_YEAR                              │         │ 'OFF'  │
│                                  YEAR                                   │         │ 'OFF'  │
│               CANDLES_CANDLES-VOLUMES_CANDLES_CANDLE_OPEN               │         │  'ON'  │
│               CANDLES_CANDLES-VOLUMES_VOLUMES_VOLUME_BUY                │         │  'ON'  │
│ MASTERS_RESISTANCES-AND-SUPPORTS_RESISTANCES_RESISTANCE_RESISTANCE1RATE │         │  'ON'  │
│ MASTERS_RESISTANCES-AND-SUPPORTS_RESISTANCES_RESISTANCE_RESISTANCE2RATE │         │ 'OFF'  │
│ MASTERS_RESISTANCES-AND-SUPPORTS_RESISTANCES_RESISTANCE_RESISTANCE3RATE │         │ 'OFF'  │
│ MASTERS_RESISTANCES-AND-SUPPORTS_RESISTANCES_RESISTANCE_RESISTANCE4RATE │         │ 'OFF'  │
│ MASTERS_RESISTANCES-AND-SUPPORTS_RESISTANCES_RESISTANCE_RESISTANCE5RATE │         │ 'OFF'  │
│     MASTERS_RESISTANCES-AND-SUPPORTS_SUPPORTS_SUPPORT_SUPPORT1RATE      │         │  'ON'  │
│     MASTERS_RESISTANCES-AND-SUPPORTS_SUPPORTS_SUPPORT_SUPPORT2RATE      │         │ 'OFF'  │
│     MASTERS_RESISTANCES-AND-SUPPORTS_SUPPORTS_SUPPORT_SUPPORT3RATE      │         │ 'OFF'  │
│     MASTERS_RESISTANCES-AND-SUPPORTS_SUPPORTS_SUPPORT_SUPPORT4RATE      │         │ 'OFF'  │
│     MASTERS_RESISTANCES-AND-SUPPORTS_SUPPORTS_SUPPORT_SUPPORT5RATE      │         │ 'OFF'  │
└─────────────────────────────────────────────────────────────────────────┴─────────┴────────┘

### Example of Dataset [Fraction of it]

* Timestamp   BTC-candle.max-24-hs-1   BTC-candle.min-24-hs-1   BTC-candle.open-24-hs-1   BTC-candle.close-24-hs-1   BTC-volume.total-24-hs-1
* 1503014400000   4371.52   3938.77   4285.08   4108.37   1199.8882639999993
* 1503100800000   4184.69   3850   4108.37   4139.98   381.3097630000001
* 1503187200000   4211.08   4032.62   4139.98   4086.29   467.0830220000002
* 1503273600000   4119.62   3911.79   4069.13   4016   691.7430599999999
* 1503360000000   4104.82   3400   4016   4040   966.6848579999996
* 1503446400000   4265.8   4013.89   4040   4114.01   1001.136565
* 1503532800000   4371.68   4085.01   4147   4316.01   787.4187530000003
* 1503619200000   4453.91   4247.48   4316.01   4280.68   573.6127399999996
* 1503705600000   4367   4212.41   4280.68   4337.44   228.10806799999992
* 1503792000000   4400   4285.54   4332.51   4310.01   350.6925850000002
* 1503878400000   4399.82   4124.54   4310.01   4386.69   603.8416160000002

### How does this Test Client App work?

This app is used to autonomously test different set of parameters to see which Machine Learnning models can produce better forecasts.

This is part of a system that also has a Test Server App and another app called the Forecast Client. The Test Server app manages a set of different Test Cases that needs to be crowd-tested.

Each Test Client app, connects to the Test Server app via webRTC. Once connected, it will enter into an infinite loop requesting new Test Cases to the Test Server.

Once a Test Case is received, the Test Client app will write 2 files at the notebooks folder (which is a shared volume with the Tensor Flow container):

* parameters.CSV
* time-series.CSV

After these files are written, the Test Client App will execute inside the TensorFlow container the Bitcoin_Factory_LSTM.py script. 

This script reads boths files, and creates a ML model using the provided parameters and the data at the time-series file. It's execution could take several minutes. Once finished, a set of results are sent back from the Python script to the Test Client app, which in turn sends via webRTC the results to the Test Server app. 

The Test Server app remembers all the test results and organizes a collection with the best crowd-sourced forecasts for each Asset / Timeframe. 

This consolidated collection with the best crowd-sourced forecasts is sent back to each Test Client as a response to their own report with the results of their latest test.  

The Test Client app once it receives this report, it send it to Superalgos so that it can be saved as a regular indicator under the Bitcoin-Factory Data Mine. The Test Client app then wait for 10 seconds and repeat the process again, requesting a new Test Case to test.

### How does the overal System Work?

As mentioned before the system consist of 3 different apps:

1. The Test Server
2. The Test Client
3. The Forecast Client

#### The Test Server

This app manages all test and forecasts cases, but it does not run the tests or do the forecasts. Everytime a test case finds a parameter combination with a lower Error for a certain Asset / Timeframe, the test case is transformed into a Forecast Case replacing the previous best performing Forecast case for that same Asset / Timeframe. This app is ran by the Bitcoin Factory. 

#### The Test Client

This app feeds itself from the Test Server with test cases. It runs each Test Case at the Tensor Flow Docker Container, reports bact to the Test Server the test results, receives the latest best-forecasts, and sends them to Superalgos to be saved as an indicator.

#### The Forecast Client

This app feeds itself from the Test Server foracast cases. A forecast case is the best known set of parameters for a certain Asseet / Timeframe. The job of this App is to recreate the model discovered by a Tester using the Test App, and once created, start forcasting with it the next candle for that Asset / Timeframe. The forecasts produced by this App are sent to the Test Server and from there distributed to the Test App users every time they test a new case, and finally they end up in their user's Superalgos data storage as indicator data. 

### Should I leave this Test Client App Running?

Yes, if you want to be receiving the crowd-sourced forecasts over time. Each new hour, you will get new forecast obtenined with the best crowd-sourced models available for each Asset / Timeframe. 

If you have this app running, you will be collecting all these forecasts and building over time historical dataset with the forecasts received. That could later be used for backtesting strategies which relies on these forecasts. 

If you already have a strategy that uses forcasts and you want to live trade with it, then you will need at least one Test Client App running to receive updated forecasts over time. If you run more than one Test Client at the same time, chances are that you will be updated with these forecasts more often, since the crowd-sourced forcasts are received after each test you make (which might take several minutes), having more than one app doing tests increases the frequency in which you get new forecasts.

### How do we know which are the best Forecasts?

Each tested model (created based on a set of parameters and a custom dataset) has a certain implied Error: the root-mean-square error (RMSE).

https://en.wikipedia.org/wiki/Root-mean-square_deviation

The whole point of crowd-testing is to find the model with the lowest % of error for a certain Asset / Time-Frame. 

Note: All forecasts are done at the Asset/USDT markets on Binance for now.

When you are running this App, you are testing certain combinations of parameters for a certain Asset / Time-Frame including a custom dataset for your specific test, which might include a certain combination of indicators data.

The crowd-sourced forecasts you receive after each test, are the ones belonging to ML models with the lowest % error for a certain Asset / Time-Frame.

### Why is this System Beautiful?

Because the precision of the forcasts can only improve over time. Think about it, once we find for instance the right set of parameters and data for BTC / 1Hs, that have for instance a 0.8 % of error, we will be forcasting with this model until the minute anyone in the crowd finds another set of parameters and data for BTC / 1Hs with a lower error, let's say 0.6, and you guess, from there on, all forcast will be done with that ML model until the day someone else finds another one with even less % error.

It might take time, but our collective intelligence can only improve over time. 

And all that finding and forecasting is 100% automated. Only computers working together. The more people join the effort, the faster we find better models, the better the forecasts become for all the people participating. Beautiful, ins't it?

Having said that, please don't expect that at the begining the forecasts will be precise. We are brute forcing the discovery of which are the best combination of parameters and data for each Asset / Timeframe and that might take a while to produce models with reasonable performance, but once we have them, we have them forever.

### Superalgos Network

The Test Client and Test Server interact in a p2p way via the Superalgos Network, that means that we can run a Test Server at home and get help to process Test Cases from anywhere in the world without the need to pay for cloud servers, and almost without limits regarding the amount of people that can help. Only one Superalgos Network Node needs to run at the Cloud, and it will take care of conecting the Client with the Server.

## Pre-Requisites

* nodejs
* npm
* git
* docker

## Superalgos Profile

To run this software you need a Superalgos Profile with the node Forecast Providers / Bitcoin Factory Forecast / Test Client Instance.

### In Detail 

For your Test Client App to work and be able to connect to the Test Server you need to:

1. The Bitcoin Factory Forecast node must be named Testnet.
2. You need a Test Client Instance for each process or instance of this Test Client App you want to keep ruuning. Name it as you like.
3. You will need to assing each Test Client Instance some SA token power if you wish to receive the best crowd-sourced predictions at the end of each of your tests. How much token power for each prediction is to be determined in the near future once the assigned token power will be checked at a future release.

Note 1: Once you add those nodes to your profile you still needs to contribute it and it needs to be merged. After that you will need to wait until the Test Server updates it's Superalgos installation that as of today is a manual task. If you are exited and would like to speed this process up, please contact me on Telegram. (@luis_fernando_molina)

Note 2: In the future, pending a deeper integration with the Superalgos Governance system, you will be able to receive SA tokens for each Test Case you have processed. We will start counting the solved Test Cases from now.

## Setup

The current version of Bitcoin Factory is already integrated into Superalgos. You need to load the Bitcoin Factory Demo Plugin workspace.

### Change the Config

After that, open the config of the Test-Client Sensor Bot Instance. It looks like this:

```sh
{
    "networkCodeName": "Testnet",
    "targetSuperalgosHost": "localhost",
    "targetSuperalgosHttpPort": 34248,
    "logTrainingOutput": false,
    "clientInstanceName": "Laptop-Lenovo-01"
}
```

* networkCodeName: We will use Testnet for now.
* targetSuperalgosHost: You can leave this with the default. If you wish to send the forecasted candles to a different instance of Superalgos, then change the host here.
* targetSuperalgosHttpPort: You can leave this with the default. If you wish to send the forecasted candles to a different instance of Superalgos, then change the port here.
* logTrainingOutput: Set it to true if you want more detail of the Machile Learning process at the console.
* clientInstanceName: IMPORTANT: Change this to match your own name created at your user profile.


Second, build the Docker Image.

### On x86 Processors

```sh
cd DockerBuild
docker build -t bitcoin-factory-machine-learning .
cd ..
```

### On xArm Processors

```sh
cd ArmDockerBuild
docker build -t bitcoin-factory-machine-learning .
cd ..
```

IMPORTANT NOTES: 

* 1. You need to have a 64 bit version of your OS, otherwise this is not going to work.
* 2. In linux you might need to add 'sudo' before the docker build command.
* 3. The dot at the end of the docker build command is mandatory.

## Usage

Run the Docker Container and then run the Test Client Task located at the Bitcoin Factory Demo Plugin Workspace. You will need 2 Terminals for that, at one of them the docker container will be running, and at the second one, you will run the Superalgos and inside the Platform, the Test-Client Task.

Once the docker container is running correctly you will see at the first terminal an ouput similar to this:

```sh
[I 12:58:36.546 NotebookApp] Writing notebook server cookie secret to /home/ubuntu/.local/share/jupyter/runtime/notebook_cookie_secret
[I 12:58:37.532 NotebookApp] Serving notebooks from local directory: /tf/notebooks
[I 12:58:37.532 NotebookApp] Jupyter Notebook 6.4.10 is running at:
[I 12:58:37.533 NotebookApp] http://aa1b305587bd:8888/?token=49c135d693e0b4d07d8c0164410ee6fc4593ac5e0578a34a
[I 12:58:37.533 NotebookApp]  or http://127.0.0.1:8888/?token=49c135d693e0b4d07d8c0164410ee6fc4593ac5e0578a34a
[I 12:58:37.533 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 12:58:37.544 NotebookApp]

    To access the notebook, open this file in a browser:
        file:///home/ubuntu/.local/share/jupyter/runtime/nbserver-1-open.html
    Or copy and paste one of these URLs:
        http://aa1b305587bd:8888/?token=49c135d693e0b4d07d8c0164410ee6fc4593ac5e0578a34a
     or http://127.0.0.1:8888/?token=49c135d693e0b4d07d8c0164410ee6fc4593ac5e0578a34a

```

At that terminal there is no further action required. 

At the Superalgos terminal, once  you run the Test Client Task, you will see, after 10 seconds an output similar to this one:

```sh
-------------------------------------------------------- Test Case # 1 / 3192 --------------------------------------------------------

Starting at this GMT Datetime:  2022-03-24T10:00:55.115Z

Parameters Received for this Test:
┌────────────────────────────────────┬─────────┬────────┐
│              (index)               │    0    │ Values │
├────────────────────────────────────┼─────────┼────────┤
│           LIST_OF_ASSETS           │  'BTC'  │        │
│         LIST_OF_TIMEFRAMES         │ '03-hs' │        │
│  NUMBER_OF_INDICATORS_PROPERTIES   │         │   5    │
│      NUMBER_OF_LAG_TIMESTEPS       │         │   8    │
│          NUMBER_OF_ASSETS          │         │   1    │
│          NUMBER_OF_LABELS          │         │   3    │
│ PERCENTAGE_OF_DATASET_FOR_TRAINING │         │   80   │
│         NUMBER_OF_FEATURES         │         │   5    │
│          NUMBER_OF_EPOCHS          │         │  300   │
│       NUMBER_OF_LSTM_NEURONS       │         │   50   │
└────────────────────────────────────┴─────────┴────────┘

```

There are no more needed actions from your side. After between 15 and 30 minutes, depending on the Test Case that was assigned to you, you will see an output like this:

```sh
Docker Python Script exited with code 0
Prediction RMSE Error: 368.83
Predictions [candle.max, candle.min, candle.close]: 43278.008,42785.055,43028.305
Enlapsed Time (HH:MM:SS): 14:29

Best Crowd-Sourced Predictions:
┌─────────┬────┬───────────┬───────────────┬─────────────────────┬─────────────────────────────────────┬─────────────────┐
│ (index) │ id │ mainAsset │ mainTimeFrame │ percentageErrorRMSE │             predictions             │ forcastedCandle │
├─────────┼────┼───────────┼───────────────┼─────────────────────┼─────────────────────────────────────┼─────────────────┤
│    0    │ 14 │   'BTC'   │    '01-hs'    │       '0.59'        │  [ 43316.723, 42906.44, 43185.24 ]  │    [Object]     │
│    1    │ 31 │   'BTC'   │    '02-hs'    │       '0.85'        │ [ 43278.008, 42785.055, 43028.305 ] │    [Object]     │
└─────────┴────┴───────────┴───────────────┴─────────────────────┴─────────────────────────────────────┴─────────────────┘
```

Once you see this at least once, that means that your Client App is running 100% well and you should leave it alone. Even if you see messages that the server is not available, don't worry, the server might need to be restarted from time to time, your app will automatically reconnect and continue processing Test Cases when they are available.

### Multiple Instances of the Test Client Task

If you wish, you can run multiple instances of the Test Client Task. Clone the current Task and attach it to the same Task Manager to have more Tasks to run. Do not forget to change the bot configuration at each task to assing a different name to each one of them. 

You will also need multiple Test Client Instances at your Superalgos User Profile. Each instance name need to match the config at the bot insdide each task. 

Only one Docker Container needs to be running even if you run more than one instance of the Test App.

Depending on your hardware, your machine might do well with 2 or 3 instances running, monitor the CPU usage to see which is the limit for your specific hardware.

When you are running more than one instance, chances are that you will get the best crowd-sourced forcasts more often.

## Instructions for each OS

For specific information on how to run the Docker Container and the App at different OS, please read the following sections:

### on Windows

Run the container with this commnad. Change the path if you did not install this App at the commands location.

```sh
docker run -it --rm --name Bitcoin-Factory-ML -v C:/Superalgos/Bitcoin-Factory/notebooks:/tf/notebooks -p 8888:8888 bitcoin-factory-machine-learning
```

Run the App:

```sh
node runTestClient TEST_CLIENT_INSTANCE_NAME
```

### on Ubuntu Server

Run the Docker Container:

```sh
sudo docker run -it --rm --name Bitcoin-Factory-ML -v ~/Bitcoin-Factory/ML-Test-Client/notebooks:/tf/notebooks -p 8888:8888 bitcoin-factory-machine-learning
```

```sh
sudo node runTestClient TEST_CLIENT_INSTANCE_NAME
```

### on Mac OS

#### File Sharing

Before running that command for the first time, you will need to share the notebooks folder.

At the Settings of the Docker App, use File sharing to allow local directories on the Mac to be shared with Linux containers. By default the /Users, /Volume, /private, /tmp and /var/folders directory are shared. As this project is outside this directory then it must be added to the list. Otherwise you may get Mounts denied or cannot start service errors at runtime.

#### File Share Settings

To add the 'notebooks' Directory: Click + and navigate to the 'notebooks' directory.

Apply & Restart makes the directory available to containers using Docker’s bind mount (-v) feature.

#### Run the Container & the App

The command to run the container on Mac should be like this (mind Your-User-Name).

```sh
docker run -it --rm --name Bitcoin-Factory-ML -v /Users/Your-User-Name/Bitcoin-Factory/ML-Test-Client/notebooks:/tf/notebooks -p 8888:8888 bitcoin-factory-machine-learning
```

Run the App:

```sh
node runTestClient TEST_CLIENT_INSTANCE_NAME
```

### On Raspbian

Early test on Raspbian has shown difficulties to build the docker image. If you manage to make it work with this OS please report back so that we update the specific instructions for it.

## How to Upgrade

The procedure to upgrade this App is the following: Open a Terminal at the ML-Test-Client folder. The you need to pull again the app repository and the WebRTC repository.

```sh
git pull
cd ML-Test-WebRTC
git pull
```

## Troubleshooting - Docker Cheat Sheet

If you get the error:

```sh
docker: Error response from daemon: Conflict. The container name "/Bitcoin-Factory-ML" is already in use by container ...
```

Use the command

```sh
docker container prune
```

to fix it.
