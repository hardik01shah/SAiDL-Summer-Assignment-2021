# Paper Implementation Task:

I attempted to implement the paper "FastDepth: Fast Monocular Depth Estimation on Embedded Systems."
The paper mainly proposes a deep CNN architecture for use in embedded systems where real time depth perseption can be facilitated.

Link:
https://arxiv.org/abs/1903.03273 

A regression based supervised learning approach to depth estimation generally follows an encoder decoder pipeline. The encoder extracts high level low-resolution features from the input image. These features are then fed into the decoder, where they are gradually upsampled, refined, and merged to form the final high-resolution output depth map. There are skip connections from the encoding to the decoding layers.

For getting familiar with encoder decoder architecture I studied the U-Net model (used for semantic segmentation). 

FastDepth uses the MobileNetv1 as the encoder. MobileNetV1 presented a class of efficient models called MobileNets for mobile and embedded vision applications which used depth wise separable convolution operations to reduce the total parameters of the network. The architecture gave promising results on the ImageNet dataset. Since FastDepth was designed keeping in mind application on embedded systems, MobileNetv1 was used as the encoder.

<img width="509" alt="img3" src="https://user-images.githubusercontent.com/61026273/129606026-cec14fc5-5f4c-4473-944d-8b15a92074df.png">


The framework used for implementation is pytorch. The encoder is not trained and pretrained parameters on the ImageNet have been used. 

For the upsampling layers the authors have proposed 4 techniques for decoding that includes using a TransConvolution operation (as used in U-Nets).

The authors have also provided a comparison of the performance when different skip connection techniques are used (addition or concatenative). The accuracy of the model and the computation time is compared with using ReNet50 and ResNet18 as the encoder.


## References:
1. https://towardsdatascience.com/review-mobilenetv1-depthwise-separable-convolution-light-weight-model-a382df364b69
2. https://arxiv.org/abs/1903.03273 
3. https://towardsdatascience.com/understanding-semantic-segmentation-with-unet-6be4f42d4b47#:~:text=The%20UNET%20was%20developed%20by,The%20architecture%20contains%20two%20paths.&text=Thus%20it%20is%20an%20end,accept%20image%20of%20any%20size.
