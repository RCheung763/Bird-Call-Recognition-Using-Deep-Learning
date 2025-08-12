## Enhancing Bird Call Recognition with Deep Learning and Advanced Preprocessing Techniques 

### Motivation

The objective of this project is to enhance the accuracy of a bird call prediction model through advanced preprocessing techniques, addressing the limitations of an initial model with a baseline accuracy of 61%. The dataset, comprising audio spectrograms, posed challenges due to variable call patterns and environmental noise. To improve performance, spectrograms were converted to Mel Spectrograms for better frequency representation, and data augmentation techniques—time shifting, added noise, and frequency masking—were applied to increase model robustness. These preprocessing steps significantly boosted model performance, achieving an accuracy of 80% (a substantial improvement over the baseline). The original model report, included in the project repository, provides further details on the initial approach. This project demonstrates the critical role of preprocessing in audio classification, offering insights into feature engineering and augmentation for complex machine learning applications.

### Data

The dataset used is a subset of a larger dataset from Xeno-Canto, which houses crowd sourced bird calls. There were 12 species of bird calls. The format of the data is stored as spectrograms, a visual representation of the audio sample. Each spectrogram in the dataset is an ‘image’ of the 2-second segment of the birdcall. The dimension of this spectrogram is 343 (time steps) x 256 (frequency bins). The number of samples for each class varied. Below is an example of a spectro gram from bird class 3: Blue Jay and class 10: Western Meadowlark.

## Methodology

The original preprocessing technique was simple, the spectrograms were padded to create a consistent lengths, the frequency bins were normalized, and the arrays were transposed to reorganize the data. The preprocessing technique that were deployed to improve performance:Converting spectrograms to Mel Spectrograms. This changes the linear frequency(Hz) to Mel scale which mimics human hearing and reduces dimensionality from 256 frequency bins to 128Time shifting is a data augmentation techniques that artificially shifts the temporal position of the sounds. This mimics natural variability, it also prevents overfitting by preventing the model from memorizing exact temporal positions.Frequency masking is a data augmentation technique that randomly removes contiguous frequency bands from spectrograms. This prevents over reliance on specific frequency bands and improves generalizability.

A sequential CNN model was built for multiclass prediction. Hypertuning parameters utilized were dropout layers, L2 regularizers, and early stopping that monitors validation loss. The data set was split into a training, test, and validation set. Since there is resampling, the splits for the improved model are done so that there is no data leakage.

## Results and Discussion

The results show significant improvement with the added preprocessing as shown below.

### Model without added preprocessing

|           | Accuracy	| Precision	| Recall | F1-Score|
|-----------|-----------|-----------|--------|---------|
|Training	  | .65       |	.72	      | .65 	 | .67     |
|Test	      | .61	      | .70	      | .61	   | .62     |

### Improved Model

|            | Accuracy |	Precision	| Recall | F1-Score |
|------------|----------|-----------|--------|----------|
| Training	 | .84	    | .85	      | .84	   | .84      |
|Test	       | .80	    | .81	      | .80	   | .80      |

