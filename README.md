# Tspin Detection

## Project Description

This Project is a Tspin Detection Model using the latest You Only Look Once Algorithm, [YOLOv8](https://docs.ultralytics.com/) . I first collected about 150 screenshots that contain tspins from 1v1 replays of the best players on tetr.io. I then used the software [Roboflow](https://roboflow.com/) to help annotate the dataset, train validate test split my dataset, resize my images, and augment dataset for a larger variety. After that I trained the YOLOv8n model with my dataset and finished the training by predicting a video of two players 1v1ing.

## Results

To test the model I used a single replay of two of the best playeres, Blaarg and Diao(Icly), to see if the model could detect the tspins in a live video, especially at the fast speeds they're playing at. While my laptop was only able to go through a single frame in .3 seconds on average,however when testing with a gpu like the one available in google colab, it was able to go through a single frame in .015 seconds on average.  

### Tested Video 

[![](https://img.youtube.com/vi/gP3fBBHqy7w/maxresdefault.jpg)](https://www.youtube.com/watch?v=gP3fBBHqy7w)

## Dependencies and How to test your own replay

Once you've downloaded the files, first make sure you have the correct package versions. To do so open up the command prompt and move to the main directory containing all of the files, then run the command **'pip install -r requirements.txt'** and wait for all of the packages to finish installing. You then can test the model on any image/video you want using the command **`yolo predict model="\runs\detect\train\weights\best.pt" source='blaarg v diao.mp4' save=True`** and replacing the source argument with the file path of your image/video. The video/image output will be available in the most recent predict director in runs/detect. The speed of the model can depend heavily on your computer and whether or not have and are using CUDA. Model has only been trained on tetr.io 1v1s, so it might not be accurate in singleplayer or on other games such as jstris or Tetris Effect.   

## Future Work

* The dataset only labels tspin doubles so potential future work would be to expand the model to detect different tspin setups such as tspin triples, super tspin doubles, etc.
* The model was only trained using screenshots of tetr.io and 1v1s specifically, so in the future I might look to expand upon this by having a larger dataset that contains images from other games like jstris, Tetris Effect, and Puyo Puyo Tetris.
* Deploying the model live so it can be used to do real time detection in 1v1s. While my laptop isn't able to do this fast enough, with a GPU it was able to do so around 60 fps which is enough to handle the speed of top players. 
* I noticed the file size seems to grow much larger after training, so doing research on if this is common for most computer vision algorithms or if there's away to reduce this. 
