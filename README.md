# Fencing_Tracking_Example

Here is a link to the [Google Drive](https://drive.google.com/drive/folders/1jS4KTCmH0EG9-OgP0DVX9s42nCZY67YI?usp=sharing) folder containing the data files.

I used ChatGPT to show how it can be used to do the vast majority of coding for a Google Colab notebook that analyzes a Fencing Action and acts as the fencing referee to determine the touch. To do this I broke the task into 3 parts, Data Collection, Detection and Tracking and Model Training.

# Data Collection

In Data Collection, I used the Red Strip, [Day 2 of European Fencing Championships](https://www.youtube.com/watch?v=BDMml_HVcz8). I used the overlay from the video to detect when touches were scored and then detected the scores using the same overlay. I then sorted the Epee and Saber clips by scores that resulted in a point and the clock reading 3:00 minutes.

# Detection and Tracking

Taking the clips from Data Collection, I used [YoloV8 by Ultralytics](https://docs.ultralytics.com/) along with [Roboflow](https://roboflow.com/) to help with the datasets, to create a custom detection model. I then used this model with some basic tracking analysis to map the paths of the fencers' bellguards. From the bellguard positions I then derived the acceleration of the bellguards and combined the bellguard x_position acceleration with the frames that the colored lights turned on into a comma separated values (csv) file. To the csv file I added on the touch for each clip that was taken from the analysis of the overlay earlier.

# Model Training

I used a Gate Recurrent Unit model as recommended by ChatGPT to input the data. The model was quickly trained, I assume to do the simplicity of the data and relatively few data inputs. I then applied the model to Clips 1,2,3 taken from the [Blue Piste](https://www.youtube.com/watch?v=AFmK9fSg-Bk) at the same event.
