# Sailing Ranking

## Context

Sailing is a competitive and popular sport throughout the world. It is an official summer olympic competition. A sailing competition takes place over one or multiple days, in which one or more races are executed during the competition. 

The goal of the competition is to accumulate the least amount of points in order to win. When a competitor crosses the finish line they are awarded the amount of points equivalent to their finishing position (the first competitor to finish gets one point and so on).

The way the finishing positions and points are being noted for each race is as follows: At the finish line an official from the jury has a notebook and writes down the unique sail number of the competitor when they cross the line. Later once the jury comes to shore they manually copy the handwritten sail numbers over to an excel sheet that handles executing the necessary calculations, and generates the new standings of the competition.

The process at the moment is labour intensive and time consuming. When people of the jury spend hours on the water and later have to spend time copying the sail number from their notebook to a computer, it is prone to long waiting time and errors.

## Goal

The goal is to take out the “analog” part of the process. Remove the notebook and remove the “double” work of the jury members. Ideally the finishing position will only need to be noted once and the competition standings should be updated immediately.

In order to achieve this the following idea has come up: Setup a software system that holds the necessary business logic to process the finishing positions and generate new standings. Replace the notebook and pen with a tablet and smart pencil to write down the finishing sail numbers. Finally, be able to send the written sail numbers to the software system to process the data.

## Dataset
The MNIST database (Modified National of Standards and Technology database) is a large database of handwritten digits that is commonly used for training various image processing systems.

The MNIST database contains 60.000 training images and 10.000 standardised testing images.

## Data Preprocessing

The MNIST database has already been through the necessary steps in order for it to be suitable for training an Artificial Intelligence model.

## Models & Tools

### PostgreSQL

PostgreSQL is a free and open source relational database management system (RDMBS). PostgreSQL is used to store the various data that is needed to make the system “work” (competitions, competitors, points etc.).

### FastAPI

FastAPI is a modern, fast, web framework for building APIs with Python. FastAPI is used to process the various data that is submitted.

### Next.js

Next.js is a flexible React Framework that gives the developer building blocks to create web applications. Next.js is used to build the user interface.

### Optical Character Recognition

I developed code that is capable of recognizing a number from an image. The code utilises OpenCV in order to find the different digits the number is composed of and returns the positions of the digits. The digits’ positions are sorted left to right and passed to a Convolutional Neural Network, implemented with Tensorflow/Keras, which recognises the number displayed. The recognised digits are concatenated together to form the original number. Last, the predicted number is compared to the available number is the database and the closest match is returned.

### Data Version Control (DVC)

DVC is a data and Machine Learning management tool that takes advantage of the existing engineering toolset (Git, IDE, CI/CD). By integrating DVC it is possible to version the different states of the dataset, it is also possible to version Machine Learning Models. Lastly, it is possible to create “pipelines” which are a sequence of steps that allow for reproducibility of the different states of the project.

### Continuous Machine Learning (CML)

CML is a product developed by the same entity that develops DVC. CML introduces more functionality on top of DVC, while DVC focuses on versioning/reproducibility of the different aspects of a machine learning project, CML focuses on integrating/automating this process with the CI/CD (DevOps) environment. There are multiple useful features that are unlocked: 1) Training a ML model directly in the CI/CD environment, 2) Testing/Evaluating a ML model directly in the CI/CD environment, 3) Generating visualisations of a ML model directly in the CI/Cd environment, 4) Comparing various “metrics” across git branches, 5) Generate a report (automatically) that contains all the previous mentioned features and 6) Setup a git runner that utilises a GPU in order to train a new ML model. Example: It is possible now to generate a report in git after a new push to a branch that includes a comparison of the accuracy of the model trained (with GPU) on the current branch to the main branch.

## Results

The result is a full stack application that utilises a Optical Character Recognition module. The application is capable of registering new competitions, competitors, races and finishing positions.

## Future Work

