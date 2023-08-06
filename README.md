# Cough Audio Signal Classification

Cough audio signal classification has been successfully used to diagnose a variety of respiratory conditions, and there has been significant interest in leveraging Machine Learning (ML) to provide widespread COVID-19 screening.

This dataset, also known as CoughVid, provides over 25,000 crowdsourced cough recordings representing a wide range of participant ages, genders, geographic locations, and COVID-19 statuses.

The goal of the project is to build a model that correctly classifies covid and healthy samples.

Source: https://www.kaggle.com/datasets/andrewmvd/covid19-cough-audio-classification


# Used Features  
After filtering data, segmenting and preparing each audio file, i extracted the MFCCS, deltas and delta-deltas from the spectrograms, to use them as features for model training.

In sound processing, the mel-frequency cepstrum (MFC) is a representation of the short-term power spectrum of a sound, based on a linear cosine transform of a log power spectrum on a nonlinear mel scale of frequency.

Mel-frequency cepstral coefficients (MFCCs) are coefficients that collectively make up an MFC.They are derived from a type of cepstral representation of the audio clip (a nonlinear "spectrum-of-a-spectrum"). The difference between the cepstrum and the mel-frequency cepstrum is that in the MFC, the frequency bands are equally spaced on the mel scale, which approximates the human auditory system's response more closely than the linearly-spaced frequency bands used in the normal spectrum. This frequency warping can allow for better representation of sound, for example, in audio compression that might potentially reduce the transmission bandwidth and the storage requirements of audio signals.

MFCCs are commonly derived as follows:

- Take the Fourier transform of (a windowed excerpt of) a signal.
- Map the powers of the spectrum obtained above onto the mel scale, using triangular overlapping windows or alternatively, cosine overlapping windows.
- Take the logs of the powers at each of the mel frequencies.
- Take the discrete cosine transform of the list of mel log powers, as if it were a signal.
- The MFCCs are the amplitudes of the resulting spectrum.

Since, Mel-frequency bands are distributed evenly in MFCC and they are much similar to the voice system of a human, thus, MFCC can efficiently be used to characterize speakers. They describes the instantaneous, spectral envelope shape of the speech signal. However, speech signals are time-variant signals and in a constant flux. Though we describe speech in linguistics as concatenated sequences of phonemes, the acoustical signal is more accurately described as a sequence of transitions between phonemes.

A common method for extracting information about such transitions is to determine the first difference of signal features, known as the delta of a feature, and the second difference, known as the delta-delta.

# Chosen Models

The dataset was used to train a Support Vector Machine (SVM), a simple Convolutional Neural Network, a Deeper CNN, a K-nearest neighbors algorithm (KNN), a Latent Dirichlet allocation (LDA) and a  Stochastic Gradient Descent (SGD).

# Results
During validation, each one of the model reached around 80% accuracy, showing a similar performance.

![Validation_accuracy_CCC](https://github.com/pmastrogiovanni/Coughvid_Signal_Classification/assets/98032774/a546cade-c983-4570-bb4f-4fbe6692e1fd)

On testing, no model was able to get past 70% accuracy, with the CNN showing the best performance, followed by the other models that reached a similar statistic.The only model that didn't reach that range is the Deep CNN, as its stayed around 42% accuracy, showing poor generalization.

![Test_accuracy_CCC](https://github.com/pmastrogiovanni/Coughvid_Signal_Classification/assets/98032774/cf87ced9-c40d-4cc9-b0d4-08fdf7d592a8)


# Limits

- The dataset was highly unbalanced, hence i needed to perform data augmentation on the audio files, producing artificial samples for the covid cases.
- Limited computational resources, which prevented the selection of additional features from the spectrograms.
- Low amount of samples with good characterization, which led to heavy filtering in the inital steps of the project.
