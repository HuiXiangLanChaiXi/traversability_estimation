# Complementary material for the submission 224 to CoRL 2017

> **All the supplemented material is presented anonymously**


> This is the **[version of the document submission](submission/submission_224.pdf)** with **high-quality figures**.

This repository provides: 
1. media material of the experiments on the real robot and real elevation maps ([media](#media)),
2. heightmaps and csv files to generate the training and evaluation datasets ([data](#data)), 
3. and the source code to each module of our traversability estimation framework ([code](#code)):
   * simulation and data generation,
   * heightmap generation, 
   * dataset generation, 
   * definition, training and evaluation of the CNN classifier,
   * generation of traversability representations such as oriented traversability maps and minimal traversability maps, 
   * and visualization of the results as 3D renderings 
   > verify the [software requirements](#software-requirements) to test the code

## Media

This is a selection of the available media of our traversability estimation framework: 

**video demonstration of the experiments on the real Pioneer 3AT robot (vimeo link)**

[![video demonstration of the experiments on the real robot](https://i.vimeocdn.com/video/643340195_640.webp)](https://vimeo.com/224311562 "Pioneer 3AT in real scenario")

**animation of the minimal traversability map for the quarry dataset (vimeo link)**

[![animation of the minimal traversability map for the quarry dataset](https://i.vimeocdn.com/video/643336616_640.webp)](https://vimeo.com/224311774 "Minimal traversability map for the quarry dataset")


**animation of the oriented traversability maps for 32 orientations on the quarry dataset (vimeo link)**

[![animation of the oriented traversability maps for 32 orientations on the quarry dataset](https://i.vimeocdn.com/video/643336777_640.webp)](https://vimeo.com/224311892 "Oriented traversability maps for the quarry dataset")


<!--**high-quality images of the evaluation heightmaps (surfaces) and of the experiments on real robots**-->


> A larger number of visualizations can be generated/found in the `code`>`visualization` section of this repository.

## Data

This folder contains the heightmaps (gray-scale images) and the csv files with the data from each simulated trajectory.


## Code

In this folder we provide several sub-folders for each module of our traversability estimation framework:

### simulation

Code for simulating the Pioneer 3AT robot on a generated heightmap. 

This code can be accessed as a docker image that setups all the needed libraries:

> `docker pull romarcg/traversability-ros-ubuntu-gazebo`

or by copying the `simulation` folder files to an existing `ros+gazebo` setup.

### heightmap generation

Contains a document explaining in detail the procedural generation of heightmaps and a script that implements such procedure.

### dataset generation

Contains a script that takes a csv file and builds a `dataframe` that is used to generate the training/evaluation/real-evaluation dataset.

### training

Contains a script that builds the CNN architecture, takes the dataset generated by the previous script and starts the network training (this task may take several hours). In addition, a report of common metrics is provided as evaluation of the trained CNN.

The model generated by this script is saved to be used in future scripts.

> An already trained model file is provided to avoid the training step.

### evaluation

This script computes oriented traversability maps and minimal traversability maps using the trained model on unseen (testing) heightmaps.

### visualization

This script processes traversability maps and generates 3D renderings to interactively examine a heightmap and its estimated map.

> A set of already generated traversability maps is provided as sample files to avoid regenerating them.


### Software requirements

In order to use the provided scripts, these are the list of requirements:

  * python 3.5.3
  * numpy 1.12.1
  * matplotlib 2.0.0
  * pandas 0.19.2
  * tensorflow-gpu 1.0
  * keras 2.0.3
  * scikit-learn 0.18.1
  * scikit-image 0.13.0
  * joblib 0.11
  * mayavi
