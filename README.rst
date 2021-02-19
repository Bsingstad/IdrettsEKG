******************************
Classification of 12-lead ECGs 
******************************

.. image:: /img/12_lead_ecg_plot.png
**Figure 1:** This plot is made by using ecg plot [#]_  and the ECG data is from the PTB Diagnostic DB [#]_. 



This project is based on the work we did in the  `PhysioNet/Computing in Cardiology Challenge 2020 <https://physionetchallenges.github.io/2020/>`_.  `This paper <https://iopscience.iop.org/article/10.1088/1361-6579/abc960>`_ [#]_ describes the Challenge and `this paper <https://physionetchallenges.github.io/2020/papers/227.pdf>`_ discribes our contribution in this challenge.


Data:
=====
The data set in this project contains 43.101 ECGs and comes from six different sources. Table 1 show the six sources.

**Table 1:** *The table lists the six different sources used in the data set in this project*

+-----------------+---------------------------------------------------+
| Data set number | Name                                              |
+-----------------+---------------------------------------------------+
| 1               | China Physiological Signal Challenge 2018         |
+-----------------+---------------------------------------------------+
| 2               | China Physiological Signal Challenge 2018 Extra   |
+-----------------+---------------------------------------------------+
| 3               | St.Petersburg Institute of Cardiological Technics |
+-----------------+---------------------------------------------------+
| 4               | PTB Diagnostics                                   |
+-----------------+---------------------------------------------------+
| 5               | PTB-XL                                            |
+-----------------+---------------------------------------------------+
| 6               | Georgia 12-Lead ECG Challenge Database            |
+-----------------+---------------------------------------------------+

Preprocessing of data:
----------------------
The data used in two different ways by the models in this project. The first method, used by the Convolutional Neural Networks, is to use the as they are from the original dataset. The second method, used by the two ensemble models, is to extract features from the ECGs and and create a table with **n** rows and **m** columns were **n** = numbers of ECG recordings and **m** = number of features. The ECG-features are extracted by using an ECG-featurizer [#]_. The featurized data can be found `here <https://github.com/Bsingstad/IdrettsEKG/blob/main/Data/ecg_data_with_labels.csv>`_ and the script for making the dataset is `here <https://github.com/Bsingstad/IdrettsEKG/blob/main/Notebooks/Featurize%20data/Featurize_PhysioNet_CinC_Challenge_Data.ipynb>`_ .


 

Get access to the data:
-----------------------
To get access to the data used in this study you can either download it from https://physionetchallenges.github.io/2020/#data or download the same data set from Kaggle. To use the codes in this repository you should sign up for a Kaggle account and get a Kaggle API token and use this to get access to the Kaggle data set from Google Colab. Google Colab Pro was used to get sufficient GPU power and enough runtime.
 
How to get your Kaggle API token:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
1. Log in to your `Kaggle account <https://www.kaggle.com/>`_ or sign up  `here <https://www.kaggle.com/account/login?phase=startSignInTab&returnUrl=%2F>`_ 
2. On the left side of the "edit profile"-button you click on the "Account"-option.   
3. Scroll down to the API-section and click "Create New API Token"-button. 
4. You will now have a file named kaggle.json. This is your API-token
5. You can upload the kaggle.json-file to the Google Colab notebook and then you are able to download datasets from Kaggle


Models:
=======
   
10-fold cross-validated models:
-------------------------------
+--------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
| Model number | Model                                                               | Link to Notebook on github                                                                                                          |
+--------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
| 1            | FCN                                                                 | `Notebook <https://github.com/Bsingstad/IdrettsEKG/blob/main/Notebooks/Models/FCNPhysioNetChallenge2020.ipynb>`_                    |
+--------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
| 2            | Encoder                                                             | `Notebook <https://github.com/Bsingstad/IdrettsEKG/blob/main/Notebooks/Models/EncoderPhysioNetChallenge2020.ipynb>`_                |
+--------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
| 3            | FCN + MLP                                                           | `Notebook <https://github.com/Bsingstad/IdrettsEKG/blob/main/Notebooks/Models/FCN_MLP_PhysioNetChallenge2020.ipynb>`_               |
+--------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
| 4            | Encoder + MLP                                                       | `Notebook <https://github.com/Bsingstad/IdrettsEKG/blob/main/Notebooks/Models/Encoder_MLP_PhysioNetChallenge2020.ipynb>`_           |
+--------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
| 5 & 6        | Encoder + FCN (and Encoder + FCN + rule-based model)                | `Notebook <https://github.com/Bsingstad/IdrettsEKG/blob/main/Notebooks/Models/Encder_FCN%2Brule_PhysioNetChallenge2020.ipynb>`_     |
+--------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
| 7 & 8        | Encoder + FCN + MLP + (and Endcoder + FCN + MLP + Rule-based model) | `Notebook <https://github.com/Bsingstad/IdrettsEKG/blob/main/Notebooks/Models/Encder_FCN_MLP%2Brule_PhysioNetChallenge2020.ipynb>`_ |
+--------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
| 9            | Ensemble model                                                      | `Notebook <https://github.com/Bsingstad/IdrettsEKG/blob/main/Notebooks/Models/EnsembleModel12lead.ipynb>`__                         |
+--------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+



Plot the cross-validation results:
----------------------------------
The results from the cross-validated models can be plotted with  `this notebook <https://github.com/Bsingstad/IdrettsEKG/blob/main/Notebooks/CVplot/boxplot.ipynb>`_  . The figures can be found `here <https://github.com/Bsingstad/IdrettsEKG/tree/main/Results>`_.


Explainable AI:
===============
+--------------+----------+---------------------------------------------------------------------------------------------------------------------+
| Model number | Model    | Link to Notebook on github                                                                                          |
+--------------+----------+---------------------------------------------------------------------------------------------------------------------+
| 1            | Ensemble | `Notebook <https://github.com/Bsingstad/IdrettsEKG/blob/main/Notebooks/Explainable%20AI/Explain%20Ensemble.ipynb>`_ |
+--------------+----------+---------------------------------------------------------------------------------------------------------------------+
| 2            | Encoder  | `Notebook <https://github.com/Bsingstad/IdrettsEKG/blob/main/Notebooks/Explainable%20AI/Explain%20Encoder.ipynb>`_  |
+--------------+----------+---------------------------------------------------------------------------------------------------------------------+

Paper:
======

The paper describing the work in this project can be found here: 


                                                                                
.. image:: https://zenodo.org/badge/DOI/10.5281/zenodo.4445257.svg
   :target: https://doi.org/10.5281/zenodo.4445257     


       
License:
========

Licensed under the `Apache 2.0 License`_

.. _Apache 2.0 License: http://www.apache.org/licenses/LICENSE-2.0

.. _NOTICE.txt: https://github.com/nedbat/coveragepy/blob/master/NOTICE.txt

.. _Apache License Version 2.0: http://opensource.org/licenses/Apache-2.0

.. |Apache2.0 license| image:: https://img.shields.io/badge/License-Apache%202.0-blue.svg
   :target: https://opensource.org/licenses/Apache-2.0
   

References:
===========

.. [#] ECG plot: https://github.com/dy1901/ecg_plot
.. [#] PTB Diagnostic DB: Bousseljot R, Kreiseler D, Schnabel, A. Nutzung der EKG-Signaldatenbank CARDIODAT der PTB über das Internet. Biomedizinische Technik, Band 40, Ergänzungsband 1 (1995) S 317 (https://physionet.org/content/ptbdb/1.0.0/)
.. [#] Perez Alday, Erick A, Annie Gu, Amit J Shah, Chad Robichaux, An-Kwok Ian Wong, Chengyu Liu, Feifei Liu, mfl. «Classification of 12-lead ECGs: the PhysioNet/Computing in Cardiology Challenge 2020». Physiological Measurement, 11. november 2020. https://doi.org/10.1088/1361-6579/abc960.
.. [#] ECG-Featurizer: https://github.com/ECG-featurizer/ECG-featurizer


Copyright |copy| 2021 Bjørn-Jostein Singstad

