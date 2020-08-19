# RF_modulation_classification
A project on RF modulation classification using different neural architectures and RF signal representations.

Table of architectures and feature types focused on in this project:
![table](https://github.com/interngithub2020/RF_modulation_classification/blob/master/pics/tablelit.png)

# Notebooks:

## data_visualisations

This notebook explores the [radioML datasets](https://www.deepsig.ai/datasets), in different data representations: constellation diagram, IQ time-series, amplitude-phase time-series and power density spectra. It also visualises the dataets with Rician Fading that I created following this [Matlab tutorial](https://www.mathworks.com/help/deeplearning/ug/modulation-classification-with-deep-learning.html).

### 2016.10A radioML
![rml](https://github.com/interngithub2020/RF_modulation_classification/blob/master/pics/radioml2016.png)

### Matlab hard dataset: Rician fading, Doppler, LO clock shift, AWGN
![hard](https://github.com/interngithub2020/RF_modulation_classification/blob/master/pics/matlab_hard.png)

### Matlab medium dataset: Rician fading, light clock shift, AWGN
![med](https://github.com/interngithub2020/RF_modulation_classification/blob/master/pics/matlab_med.png)

### Matlab easy dataset: AWGN
![easy](https://github.com/interngithub2020/RF_modulation_classification/blob/master/pics/matlab_easy.png)

## time-series_classification

This notebook builds neural architectures from literature that performed quite well for the task of RF modulation classification and trains them on the 2016.10A radioML dataset. The architectures tried are basic CNN, Inception, ResNet, CLDNN and LSTM. I trained the models with IQ and amplitude-phase (AP) time-series and compared the results. CLDNN-AP was found to be the best performing.

### Classification accuracy over SNR of different architectures
![time-series_snracc](https://github.com/interngithub2020/RF_modulation_classification/blob/master/pics/timeseries_snracc.png)

### Confusion matrices of IQ trained vs AP trained model
![iq-ap-cm](https://github.com/interngithub2020/RF_modulation_classification/blob/master/pics/iq_ap_cm.png)

## constellation_classification

This notebook explores constellation image representations with different resolutions and colour schemes. It was found that increasing resolution improved performance while colour didn't have much of an effect. Be careful of memory usage.

### Examples of constellation images with different resolutions and colours
![constel_img](https://github.com/interngithub2020/RF_modulation_classification/blob/master/pics/constel_res_col.png)

### Classification accuracy over SNR of different constellation images trained models
![constel_snracc](https://github.com/interngithub2020/RF_modulation_classification/blob/master/pics/constel_eval.png)

## model_evaluation_radioml

This notebook compares the best performing time-series and constellation models on the 2016.10A radioML dataset. CLDNN-AP outperforms the constellation models, and a model combining both ResNet-IQ and CLDNN-AP performs well in both low and high SNR conditions.

### Classification accuracy over SNR and Confusion Matrices of best performing models
![rml_eval](https://github.com/interngithub2020/RF_modulation_classification/blob/master/pics/combined_snracc.png)

## mode_evaluation_Matlab

This notebook compares the best performing models on a realistic but more difficut dataset I generated from Matlab (see report for details on data). Here, the models performed a lot worse especially for higher order modulations like QAMs and PSKs, and the constellation model performed significantly better than IQ models for these high order constellations. This suggests the potential of having a model that have both time-series and constellation images as input. Also, I found that models trained on one Matlab dataset didn't perform well on another, which isn't a good sign for modulation recognition in real-life.

### Classification accuracy over SNR on hard dataset
![hard_snracc](https://github.com/interngithub2020/RF_modulation_classification/blob/master/pics/hard_snracc.png)

### Confusion matrices on hard dataset
![hard_cm](https://github.com/interngithub2020/RF_modulation_classification/blob/master/pics/hard_cm.png)

# References
[1] T. O’Shea and N. West, “Radio machine learning dataset generation with gnu
radio,” Proceedings of the GNU Radio Conference, vol. 1, no. 1, 2016. [Online]. Available:
https://pubs.gnuradio.org/index.php/grcon/article/view/11
[2] T. J. O’Shea and J. Corgan, “Convolutional radio modulation recognition networks,” CoRR,
vol. abs/1602.04105, 2016. [Online]. Available: http://arxiv.org/abs/1602.04105
[3] N. E. West and T. J. O’Shea, “Deep architectures for modulation recognition,” CoRR, vol.
abs/1703.09197, 2017. [Online]. Available: http://arxiv.org/abs/1703.09197
[4] M. Kulin, T. Kazaz, I. Moerman, and E. D. Poorter, “End-to-end learning from spectrum data:
A deep learning approach for wireless signal identification in spectrum monitoring applications,”
CoRR, vol. abs/1712.03987, 2017. [Online]. Available: http://arxiv.org/abs/1712.03987
23[5] T. J. O’Shea, T. Roy, and T. C. Clancy, “Over the air deep learning based
radio signal classification,” CoRR, vol. abs/1712.04578, 2017. [Online]. Available:
http://arxiv.org/abs/1712.04578
[6] S. Rajendran, W. Meert, D. Giustiniano, V. Lenders, and S. Pollin, “Distributed deep
learning models for wireless signal classification with low-cost spectrum sensors,” CoRR, vol.
abs/1707.08908, 2017. [Online]. Available: http://arxiv.org/abs/1707.08908
[7] S. Peng, H. Jiang, H. Wang, H. Alwageed, and Y. Yao, “Modulation classification using
convolutional neural network based deep learning model,” in 2017 26th Wireless and Optical
Communication Conference (WOCC), 2017, pp. 1–5.
[8] Y. Wang, M. Liu, J. Yang, and G. Gui, “Data-driven deep learning for automatic modulation
recognition in cognitive radios,” IEEE Transactions on Vehicular Technology, vol. 68, no. 4,
pp. 4074–4077, 2019.
[9] B. Tang, Y. Tu, Z. Zhang, and Y. Lin, “Digital signal modulation classification with data
augmentation using generative adversarial nets in cognitive radio networks,” IEEE Access,
vol. 6, pp. 15 713–15 722, 2018.
