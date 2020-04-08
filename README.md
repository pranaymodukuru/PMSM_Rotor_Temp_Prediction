# PMSM Rotor Temperature Prediction

### Predicting Rotor Temperature of a Permanent Magnet Synchronous Motor(PMSM) using a Convolutional Neural Network(CNN)

#### 1. Problem Statement

The rotor temperature of any motor is difficult to measure as it is a rotating part. Placing any sensors to measure this difficult to measure temperature would result in increase in costs and also increase the weight of the motor. In the era of electric vehicles, electric drives have become common in automotives and a lot of research is ongoing to reduce the weight of the motors in order to increase the efficiency of electric cars.

Measurement of quantities like temperature, torque of the rotor is important in order to design control systems to effectively control the motor. Many statistical based approaches have been studied in estimating the values of temperatures and torque, but these approaches require domain knowledge and often are different for different motors and different operating conditions. There is no universal approach towards estimating these values.

With the advent of Deep Learning, methods have been proposed to use deep learning approaches to predict the sensor values. The goal of the project is to efficiently predict the rotor temperature of a permanent magnet synchronous motor (PMSM), as it is usually difficult to measure the rotor temperature. This kind of prediction helps to reduce the amount of equipment
that is to be mounted on to the motor to measure the temperature.


#### 2. Data Description

This project uses the electric-motor-temperature dataset to predict the rotor temperature of a motor. The dataset and its description is available here: https://www.kaggle.com/wkirgsn/electric-motor-temperature

A brief description of data attributes:

* **Ambient** - Ambient temperature
* **Coolant** - Coolant temperature
* **u_d** - Voltage d-component (Active component)
* **u_q** - Voltage q-component (Reactive component)
* **Motor_speed** - Speed of the motor
* **Torque** - Torque induced by current
* **i_d** - Current d-component (Active component)
* **i_q** - Current q-component (Reactive component)
* **pm** - Permanent Magnet Surface temperature
* **Stator_yoke** - Stator yoke temperature
* **Stator_tooth** - Stator tooth temperature
* **Stator_winding** - Stator Stator_winding temperature
* **Profile_id** - Measurement Session id

Target features are **pm**, **Torque**, and **Stator_*** temperatures.

#### 3. Data Preparation

The data has been divided into sequences of certain length. For example, A series of values collected from all the sensors over a time period of 10 seconds is taken as a sequence and the target value for this sequence is the temperature value of the next instance.

This way we can give the raw sensor values to the model and predict the temperature values. Although there are four interesting targets here. Only one of them is used as a target variable in this project.

#### 4. Modelling and Evaluation

* Algorithm used - 1-D Convolutional Neural Network

The sequence of sensor values are given as an input to the CNN and the output of CNN is taken as temperature.

* Evaluation Metric - RMSE

Since the target variable is a continuous variable, regression evaluation metric RMSE (Root Mean Squared Error) and R2 Score (Coefficient of Determination) have been used.

#### 5. Results

##### Loss vs Epoch
![Loss vs Epoch](https://github.com/pranaymodukuru/PMSM_Rotor_Temp_Prediction/blob/master/imgs/losses.png)
#### Predictions
![Predictions](https://github.com/pranaymodukuru/PMSM_Rotor_Temp_Prediction/blob/master/imgs/predictions.png)

#### 6. References
1. https://www.kaggle.com/wkirgsn/electric-motor-temperature
