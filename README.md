# Industrial Audio
December 21, 2019

Contents
This repo contains jupyter notebooks which demonstrate classifying industrial audio with music domain features.  
This source data used for these classifications come from the 'VROOM' dataset.  This data can be found at this address https://github.com/SingingData/Vroom. We presented this work at the Women in Machine Learning workshop poster session at the opening reception of NeurIPS 2019 in Vancouver.  The NeurIPS Poster is here.  NeurIPS poster is here. https://github.com/SingingData/Industrial-Audio-Classification/blob/master/Media/Ryan-NeurIPS-poster.pdf

Motivation
In a manufacturing setting, sounds that are heard on the factory floor provide unmistakable information about whether a machine or 
tool is working correctly or not.  Domain experts working in manufacturing environments rely on their sense of hearing, and their 
knowledge of what sounds right or wrong to help them identify quality problems based on the sound pitch, rhythm, timbre and other characteristics. Using machine learning to classify these sounds has broad applications to automate the manual quality recognition work currently being done.  In application, we found we could use the same techniques to distinguish between models of motors or between specific motors.

The Approach
We use the Keras functional API with multi-input convnet model combining 1D representations of pitch estimations using pretrained model ‘CREPE’ using time domain waveform, and CQT or STFT 2D transforms.  We have applied this method to distinguishes motorized tool quality classes in industrial settings to classify welding quality and machining settings.  We have also applied this method to distinguish between motor sounds as varied as models of aircrafts landing at LAX and specific ferry boats in operation on Puget Sound

Featurization of Pitch and Timbre
We characterize pitch and timbre through frequency domain changes over time, represented by 2D spectrograms based on either the Constant Q Transform (CQT) or the Short-Time Fourier Transform (STFT)
CQT is a time-frequency analysis method with higher frequency resolution at lower frequencies and higher time resolution towards higher frequencies3 better capturing both pitch and timbre* 
STFT determines the sinusoidal frequency and phase content of local sections of the signal
CREPE transfer learns fundamental frequency using a pre-trained pitch model. 

Data Augmentation
Scarce labeled data of expert quality, and variation between human experts, led us to explore alternative data augmentation techniques. We applied time and frequency masking of the 2D spectrograms with Specaugment.  We found this augmentation technique gave us the added benefit of stabilizing learning during training. We also added volume reduction and white noise to augment our source data. 

References
We leveraged and were inspired by some prior work.  I list here some of the key influences. 
(1) CREPE: A Convolutional Representation for Pitch Estimation, Jong Wook Kim, Justin Salamon, Peter Li, Juan Pablo Bello, Feb 17, 2018 

(2) Echolocation: Measurement of Pitch versus Distance for Sounds Reflected on a Flat Surface, The Journal of the Acoustical Society of Amer, May 1964, Bassett and Eastmond  

(3) TimbreTron: A WaveNet(CycleGAN(CQT(Audio))) Pipeline for Musical Timbre Transfer, Huang, Li, Anil, Bao, Oort, Grosse, May 2, 2019 

(4) GANSynth: Adversarial Neural Audio Synthesis, Jesse Engel, Kumar Krishna 
Agrawal, Shuvo Chen, Ishaan Gulrajani, Chris Donahue, Adam Roberts 

(5) Air filter particulate loading detection using smartphone audio and optimized ensemble classification, Engineering Applications of Artificial Intelligence, Siegel, Bhattacharyyam, Sumeet, Sanjay, and Sarma 

(6) Makcedward: makcedward GitHub repo and python package nlpaug and SpecAugment: A Simple Data Augmentation Method for Automatic Speech Recognition, Daniel S. Park, William Chan, Yu Zhang, Chung-Cheng Chiu, Barret Zoph, Ekin Cubuk, Quoc Le Apr, 2019

(7) Comparison of Time-Frequency Representations for Environmental Sound Classification using Convolutional Neural Networks, Muhammad Huzaifah, June, 2017
