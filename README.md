# Style-Transfer

Higher layers in the network capture the high-level content in terms of objects and their arrangement in the input image but do not constrain the exact pixel values of the reconstruction. In contrast, reconstructions from the lower layers simply reproduce the exact pixel values of the original image. We, therefore, refer to the feature responses in higher layers of the network as the content representation. To obtain a representation of the style of an input image, we use a feature space originally designed to capture texture information. This feature space is built on top of the filter responses in each layer of the network. It consists of the correl.ations between the different filter responses over the spatial extent of the feature maps.

![image](https://user-images.githubusercontent.com/47561760/192529618-455bb9f6-109b-497b-b36e-1bece0ce60d7.png)

[Paper Link](https://arxiv.org/abs/1508.06576)

# Loss

## Content Loss

This is based on the intuition that images with similar content will have similar representation in the higher layers of the network.

![image](https://user-images.githubusercontent.com/47561760/192530678-3899db2f-1985-40a0-a69f-f7eef6b01f64.png)

## Style Loss

By style, we basically mean to capture brush strokes and patterns. So we mainly use the lower layers, which capture low-level features.
The intuition behind using a gram matrix is that we’re trying to capture the statistics of the lower layers.

![image](https://user-images.githubusercontent.com/47561760/192530701-9721f576-12a0-428a-ac09-646dc682970e.png)

## Total Loss

![image](https://user-images.githubusercontent.com/47561760/192530743-cd400401-8acc-481e-b2f6-0457ad10b2ab.png)


# Train
Trainer class Does the main part of code which is training model, plot the training process and save model each n epochs.

I Defined `Adam` Optimizer with learning rate 0.0002.

Each generative model training step occurse in `train_generator` function, descriminator model training step in `train_descriminator` and whole trining process in 
`train` function.

## Some Configurations
 
*   You can set epoch size : `EPOCHS` and batch size : `BATCH_SIZE`.
*   Set `device` that you want to train model on it : `device`(default runs on cuda if it's available)
*   You can set one of three `verboses` that prints info you want => 0 == nothing || 1 == model architecture || 2 == print optimizer || 3 == model parameters size.
*   Each time you train model weights and plot(if `save_plots` == True) will be saved in `save_dir`.
*   You can find a `configs` file in `save_dir` that contains some information about run. 
*   You can choose Optimizer: `OPTIMIZER` 

# Results

|  Original Image  |  Style Image  |  Result  |
| ------------- | ------------- | ------------- |
|![sobhan](https://user-images.githubusercontent.com/47561760/192532008-48388588-a7d1-4438-b287-1e45f927c2b2.jpg)|![style Image2](https://user-images.githubusercontent.com/47561760/192532357-aad436ce-6b4b-400e-ae51-bc50c6b3700b.jpg)| ![styleTransfer](https://user-images.githubusercontent.com/47561760/192532920-4e369584-fc76-4b51-9b4a-0cbdb5c7d5f4.png)|
|![sobhan](https://user-images.githubusercontent.com/47561760/192532008-48388588-a7d1-4438-b287-1e45f927c2b2.jpg)|![style Image3](https://user-images.githubusercontent.com/47561760/192533233-646d6fd3-bb76-4cad-875f-c4960896d691.jpg)|![image](https://user-images.githubusercontent.com/47561760/192533221-bf235eef-f61c-4a02-b3a9-2870adb065f1.png)|
|![sobhan](https://user-images.githubusercontent.com/47561760/192532008-48388588-a7d1-4438-b287-1e45f927c2b2.jpg)|![style Image1](https://user-images.githubusercontent.com/47561760/192533420-061ee242-fccb-45ef-84e4-2133eabee5b5.jpg)|![epoch-4890-plot](https://user-images.githubusercontent.com/47561760/192533654-4bf186bf-d63a-4342-9381-2a3904c89cef.png)|








