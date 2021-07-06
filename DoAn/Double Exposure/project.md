# **Final Project: Double Exposure**
## Double Exposure
- Double Exposure is a problem that applies blending techniques where two overlapping images create an interesting and unique effect. It is often referred to as the multiple exposure effect. In photography and film, multiple exposure is a technique in which the camera shutter is opened multiple times to expose the film image multiple times, often for different images. The resulting image contains images that are superimposed on the original image to create a blur effect.
- This effect is widely used in posters, magazines and advertising prints to create dramatic visual effects.
- Input: input image, mask and background.
- Output: an output image merged with the background at the mask position.

![alt text](https://github.com/ndtuan10/DeepLearning_CS431.L21.KHCL/blob/main/DoAn/Double%20Exposure/Image/double-exposure.png)

## Implementation:
- Step 1: Image matting
  - In order to obtain a highly detailed portrait mask, so image segmentation was one of the method that our team mentioned first. The task of image segmentation is to train a neural network to generate a pixel-wise mask for the image. This helps to understand the image at a much lower level, i.e., the pixel level.
  - During segmentation there will be borders around the object that remain when we separate from the background. This happens when the pixels of the background are very close to the pixels of the object image, resulting in this phenomenon. Image matting is a more advanced method of helping to identify specific masks as it can separate very detailed contours around the object. It is applied in image processing, video editing and filmmaking.
  - We decided to choose MODNet network architecture for image matting technique. 
    - This is MODNet's repository:  https://github.com/ZHKKKe/MODNet
    - This is MODNet's paper: https://arxiv.org/pdf/2011.11961.pdf
   
 ![alt text](https://github.com/ndtuan10/DeepLearning_CS431.L21.KHCL/blob/main/DoAn/Double%20Exposure/Image/MODNet-architecture.png)
  
- Step 2: Image blending
  - After obtaining a highly detailed mask from the matting technique, we used blending to blend mask and background to achieve the desired output image.
  - About blending technique we apply the following formula: blend_image = (1-α) * obj + α * effect * mask (with α=0.3).
- Step 3: Deploy to a web application using Flask.
## About web application
- Idea:
  - Input: The image you want to use the effect (original image), image effect, choose the background color.
  - Output: Image after applying the effect.
  - Then we build a web app using Flask.
- Libraries:
  - cv2: library of Python is designed to solve CV problems (https://opencv.org/releases/)
  - numpy: package for scientific computing with Python (https://numpy.org/)
  - PIL: as known as pillow, Python Imaging Library (https://pypi.org/project/Pillow/)
  - Flask: a micro web framework written in Python (https://flask.palletsprojects.com/en/2.0.x/)
  - Pytorch: an open source machine learning library based on the Torch library (https://pytorch.org/docs/stable/index.html)
  - Torchvision: a library for Computer Vision that goes hand in hand with PyTorch (https://pytorch.org/vision/stable/index.html)
  - Flask_bootstrap: packages Bootstrap into an extension that mostly consists of a blueprint named ‘bootstrap’ (https://pythonhosted.org/Flask-Bootstrap/)
  - Flask_colorpicker: a flask extension to add Spectrum jQuery color picker (https://github.com/mrf345/flask_colorpicker)

- Implementation:
  - Step 1: Input image.
  
  ![alt text](https://github.com/ndtuan10/DeepLearning_CS431.L21.KHCL/blob/main/DoAn/Double%20Exposure/Image/input_image.jpg)
  
  - Step 2: Background image.
  
  ![alt text](https://github.com/ndtuan10/DeepLearning_CS431.L21.KHCL/blob/main/DoAn/Double%20Exposure/Image/background.jpg)
  
  - Step 3: Choose color from color picker.
  
  ![alt text](https://github.com/ndtuan10/DeepLearning_CS431.L21.KHCL/blob/main/DoAn/Double%20Exposure/Image/color%20picker.png)
  
  - Step 4: Use image matting to get a highly detailed mask.
  
  ![alt text](https://github.com/ndtuan10/DeepLearning_CS431.L21.KHCL/blob/main/DoAn/Double%20Exposure/Image/mask.png)
  
  - Step 5: Use image blending to blend the mask with the background for the output image.
  
  ![alt text](https://github.com/ndtuan10/DeepLearning_CS431.L21.KHCL/blob/main/DoAn/Double%20Exposure/Image/output_image.png)

- You can find source code in this repostory: https://github.com/ndtuan10/DoubleExposure
- You can find video demo for web app: https://github.com/ndtuan10/DeepLearning_CS431.L21.KHCL/tree/main/DoAn/Double%20Exposure
