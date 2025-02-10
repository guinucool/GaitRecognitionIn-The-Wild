# WALK ON: GAIT RECOGNITION IN-THE-WILD

## Introduction

Using deep learning based techniques it is possible to identify subjects from gait information (accelerometer, gyroscope, image capturing, videos, etc...).
This information, nowadays, is even more easily obtainable through the smartphones that every individual has on their pockets.

## Objective

The objective of this project is to develop a deep learning model that is capable of identifying individuals given their gait information collect from their
mobile devices (accelerometer or gyroscope).

## Results

### Step-Interpolated Datasets

#### CNN Model

| Treatment  | Dataset 1 Accuracy | Dataset 1 Loss | Dataset 2 Accuracy | Dataset 2 Loss |
|------------|---------------------|---------------|---------------------|---------------|
| No Treatment    | 0.9388                 | 0.7136           | 0.9708                 | 0.5053           |
| Normalization of Steps    | ...                 | ...           | 0.9611                 | 0.4568           |
| Normalization of Separated Steps    | ...                 | ...           | 0.9537                 | 0.2666           |

#### LSTM Model

| Treatment  | Dataset 1 Accuracy | Dataset 1 Loss | Dataset 2 Accuracy | Dataset 2 Loss |
|------------|---------------------|---------------|---------------------|---------------|
| No Treatment    | 0.9249                 | 0.9446           | 0.9724                 | 0.3117           |
| Treat 2    | ...                 | ...           | 0.9483                 | 0.3543           |
| Normalization of Separated Steps    | ...                 | ...           | 0.9520                 | 0.3568           |

#### CNN + LSTM Model

| Treatment  | Dataset 1 Accuracy | Dataset 1 Loss | Dataset 2 Accuracy | Dataset 2 Loss |
|------------|---------------------|---------------|---------------------|---------------|
| No Treatment    | 0.9374                 | 1.0442          | 0.9729                 | 0.3273           |
| Treat 2    | ...                 | ...           | 0.9568                 | 0.9161           |