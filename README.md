# STAC-Overflow
1st place solution for STAC Overflow: Map Floodwater from Radar Imagery hosted by Microsoft AI for Earth
https://www.drivendata.org/competitions/81/detect-flood-water/


## Disclaimer
Many __thanks to the organizers from Driven Data and Microsoft AI for Earth__ for such an interesting competition and to the participants for the intense struggle until the last minutes!

If this solution seemed useful to you, be sure to share ⭐️

(the channel is in Russian, but we can discuss something in English)


## About the idea of the solution

Initially, I understood that I would not be able to build a super complex neural network, because either there was not enough knowledge or there was not enough computing power.

Therefore, the only chance to win was to come up with a simpler method for determining flooding. To do this, I studied articles about how waterlogging is determined now. There were neural network methods, but there were also mathematical methods. From which I concluded that in addition to segmentation by a neural network, you can try to determine the flooding pixel by pixel by some formula.

But since I am a "cool" data scientist 🦧, I did not output the formula manually, but trained ML models – Catboostclassifier, which solved the binary classification problem on pixel-by-pixel data.

Before that, I also trained the Unet models.

Further, I noticed that the models often do not fill the necessary zones, rather than overfill. Therefore, I combined the predictions of these two approaches, taking their maxima, not the average.

And as you can see, this approach worked and brought me such an important victory! 🥳

You can see other notes about the solution in the jupyter-notebooks.

## Solution plan


1. __load_external_data.ipynb__ 

This notebook is downloading additional data from Planetary Computer. Spoiler: Nasadem band is an incredibly important


2. __catboost_model.ipynb__ 

This shows the preparation of pixel-by-pixel data and the training of CatBoostClassifier models on them.


3. __unet_model.ipynb__ 

Here is a classic segmentation approach using neural networks with the Unet architecture with EfficientNet backbone.


4. __compare_methods.ipynb__ 

This notebook shows a comparison of the results of the two approaches and their combination.
