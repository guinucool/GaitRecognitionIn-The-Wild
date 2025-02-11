# WALK ON: GAIT RECOGNITION IN-THE-WILD

## Introduction

With the growing use of technology in modern days, it is rare to see someone who doesn't carry a piece of it nowadays.

Either if it is a cellphone or a smartwatch, these devices have a lot of sensors that allow them to capture information regarding the outside world and how the user interacts with it.

This gait information can later be used to identify the activity of a user during a certain period of time or even identify a user itself.

Using deep learning based techniques it is possible to achieve these objectives using gait information like accelerometer, gyroscope, image capturing, videos, etc...

## Objective

The objective of this project is, therefore, to develop a deep learning technique that is capable of identifying individuals given their gait information collected from their
mobile devices (accelerometer and gyroscope).

These methods could be used for a variety of purposes and different techniques will be used in order to study which one better fits each type of purpose and each type of data.

### Purposes

During the development of the project the following purposes will be kept in mind:

- Identifying if the individual carrying the device is the usual user (in case of stealing);

- Authentication of an individual in restricted areas (if the information transmitted by their smart phone corresponds to some authorized individual).

## Feature Analysis

In order to achieve these goals, a few datasets were considered, in order to perceive how different type of collected information can affect the identification of the users.

In the real world, most of the information is noisy and incomplete and, therefore, it is not possible to assume that optimal samples will always be available.

Both optimal and suboptimal information will be used in order to better understand how the values correlate.

### Datasets

The considered datasets are provided by [1], which is a study with similar goals to the ones considered in this project.

The first and second datasets provide perfect information. They come divided in samples of two steps (which by [1] are consireded optimal for user identification) which correspond to some user.

The third and forth datasets provide imperfect real information. They are divided in samples of 2.56 seconds collected from the devices from each individual.

The first and third datasets provide information on 118 subjects, using sample overlap to extend the dataset (sample might have moments from other samples), while the other two datasets provide information on 20 subjects, but unique samples (no overlaps).

## Feature Treatment

As the information provided by the datasets already has a good treatment level (only including the steps and being in a small time frame), the treatment done will have the objectives of adapting the information to the goals of the project and of trying to improve the performance of the models.

A series of procedures will be done and studied individually in order to better understand their necessity and how they adapt to the goal.

### Signal Pre-Processing

The first procedure will be to pre process the signal. This consits of an upsampling and a filtering of the sample in order to better recognize the steps and eliminate noise.

This step is not required for the samples of the first two datasets since they are already only two steps, but might be useful for the other two datasets since they are captured in a fixed-time length.

### Step Exctraction

This second procedure will only be applied to the first two datasets.

The goal of this exctraction is to evaluate ether single step user identification is feasable, since it is easier to exctract single steps from more smaller and limited limited samples than two consecutive steps.

### Reference System Normalization

Even though all of the samples displayed in these datasets are captured by the same device per individual, it might not always be the case in future evaluations.

It might be required to identify an individual whose gait information is only known from previous devices and, therefore, training the models with a normalized reference system will provide information for situations where that might happen.

This procedure, therefore, intends to normalize every sample into a common reference system.

### Sample Normalization

This last step is not so relevant for data alteration, it only is necessary to uniformize the data previously treated in order for it to be ready to be fed into the learning models.

Every sample will be translated into a 200 frame sample and, in case of, steps will be rejoined or separated into different samples in order to test the different model performances.

## Neural Network Models

Given the data treatment procedures, all is left is defining models for identifying users.

Three models were considered for the goals of this project:

- CNN - Convolutional Neural Network - good at identifying patterns in fixed samples

- LSTM - Long Short-Term Memory Neural Network - good at identifying time patterns in time derived samples

- CNN + LSTM - a cojoined network based on the previous two.

The first performance results acquired on the training were based on a 50 Epoch and 32 Batch-Size approach, but were switch to a 20/30 Epoch and 32 Batch-Size approach, due to similar performance and time constraints.

---

[1] Gadaleta, Matteo, and Michele Rossi. "Idnet: Smartphone-based gait recognition with convolutional neural networks." Pattern Recognition 74 (2018): 25-37.

## Results

### Step-Interpolated Datasets

#### CNN Model

| Treatment | Dataset 1 Accuracy | Dataset 1 Loss | Dataset 2 Accuracy | Dataset 2 Loss |
|-|-|-|-|-|
| No Treatment | 0.9388 | 0.7136 | 0.9708 | 0.5053 |
| Faster Training | ... | ... | ... | ... |
| Normalization of Steps | ... | ... | 0.9611 | 0.4568 |
| Normalization of Separated Steps | ... | ... | 0.9537 | 0.2666 |

#### LSTM Model

| Treatment | Dataset 1 Accuracy | Dataset 1 Loss | Dataset 2 Accuracy | Dataset 2 Loss |
|-|-|-|-|-|
| No Treatment | 0.9249 | 0.9446 | 0.9724 | 0.3117 |
| Faster Training | ... | ... | ... | ... |
| Normalization of Steps | ... | ... | 0.9483 | 0.3543 |
| Normalization of Separated Steps | ... | ... | 0.9520 | 0.3568 |

#### CNN + LSTM Model

| Treatment | Dataset 1 Accuracy | Dataset 1 Loss | Dataset 2 Accuracy | Dataset 2 Loss |
|-|-|-|-|-|
| No Treatment | 0.9374 | 1.0442 | 0.9729 | 0.3273 |
| Faster Training | ... | ... | ... | ... |
| Normalization of Steps | ... | ... | 0.9568 | 0.9161 |
| Normalization of Separated Steps | ... | ... | 0.9553 | 0.4182 |

### Fixed Time-Length Datasets

#### CNN Model

| Treatment | Dataset 3 Accuracy | Dataset 3 Loss | Dataset 4 Accuracy | Dataset 4 Loss |
|-|-|-|-|-|
| No Treatment | 0.9301 | 0.7101 | 0.9830 | 0.1671 |
| Faster Training | 0.9281 | 0.7886 | 0.9696 | 0.3472 |
| Pre-Process | 0.8863 | 1.2390 | ... | ... |
| Normalization | ... | ... | ... | ... |

#### LSTM Model

| Treatment | Dataset 3 Accuracy | Dataset 3 Loss | Dataset 4 Accuracy | Dataset 4 Loss |
|-|-|-|-|-|
| No Treatment | 0.9311 | 0.7141 | 0.9690 | 0.3178 |
| Faster Training | 0.9238 | 0.6131 | ... | ... |
| Pre-Process | ... | ... | ... | ... |
| Normalization | ... | ... | ... | ... |

#### CNN + LSTM Model

| Treatment | Dataset 3 Accuracy | Dataset 3 Loss | Dataset 4 Accuracy | Dataset 4 Loss |
|-|-|-|-|-|
| No Treatment | 0.9328 | 1.0914 | ... | ... |
| Faster Training | 0.9281 | 0.9809 | ... | ... |
| Pre-Process | ... | ... | ... | ... |
| Normalization | ... | ... | ... | ... |

### Evaluation

Examining all the performance results

## Conclusion and Future Perspective
