# Fencing Tracking Example

The purpose of this project is to showcase how ChatGPT can serve as a valuable programming aid, particularly when working with unfamiliar libraries.

Here is a link to the [Google Drive folder](https://drive.google.com/drive/folders/1jS4KTCmH0EG9-OgP0DVX9s42nCZY67YI?usp=sharing) containing the data files.

I utilized ChatGPT to demonstrate how it can effectively handle the majority of coding tasks in a Google Colab notebook that analyzes a Fencing Action and acts as a fencing referee to determine touches. To accomplish this, I divided the project into three main sections: Data Collection, Detection and Tracking, and Model Training.

## Data Collection

For Data Collection, I leveraged footage from the Red Strip captured during [Day 2 of the European Fencing Championships](https://www.youtube.com/watch?v=BDMml_HVcz8). Using the overlay from the video, I detected instances when touches were scored and extracted the corresponding scores. Next, I sorted the Epee and Saber clips based on scores resulting in a point and when the clock read 3:00 minutes.

## Detection and Tracking

Using the clips obtained during Data Collection, I employed [YoloV8 by Ultralytics](https://docs.ultralytics.com/) in conjunction with [Roboflow](https://roboflow.com/) to assist with dataset management and create a customized detection model. Subsequently, I utilized this model, along with basic tracking analysis, to trace the paths of the fencers' bellguards. By analyzing the bellguard positions, I derived the acceleration of the bellguards and combined the bellguard x_position acceleration with the frames when the colored lights turned on. This information was then saved in comma-separated values (CSV) files. Additionally, I appended the touch data for each clip, which was obtained from the overlay analysis conducted earlier.

## Model Training

Following the recommendations of ChatGPT, I employed a Gate Recurrent Unit (GRU) model to process the collected data. Due to the simplicity of the data and a relatively small number of inputs, the model trained quickly. Subsequently, I applied the trained model to analyze Clips 1, 2, and 3, which were extracted from the [Blue Piste footage](https://www.youtube.com/watch?v=AFmK9fSg-Bk) captured during the same event.

By following this approach, I demonstrated how ChatGPT can be a valuable asset in automating various aspects of a fencing analysis workflow.
