## Generative AI and Its Applications

Generative AI is one of the biggest recent advancements in artificial intelligence because of its ability to create new things.

### Discriminative vs. Generative Models
- **Discriminative Model:** Aims to answer the question, "If I'm looking at some data, how can I best classify this data or predict a value?" For example, we could use discriminative models to detect if a camera was pointed at a cat. As we train this model over a collection of images (some of which contain cats and others which do not), we expect the model to find patterns in images which help make this prediction.
- **Generative Model:** Aims to answer the question, "Have I seen data like this before?" In our image classification example, we might still use a generative model by framing the problem in terms of whether an image with the label "cat" is more similar to data you’ve seen before than an image with the label "no cat." However, generative models can be used to support a second use case. The patterns learned in generative models can be used to create brand new examples of data which look similar to the data it has seen before.

### Generative AI Models
In this lesson, you will learn how to create three popular types of generative models: generative adversarial networks (GANs), general autoregressive models, and transformer-based models. Each of these is accessible through AWS DeepComposer to give you hands-on experience with using these techniques to generate new examples of music.

#### Autoregressive Models
- **Autoregressive Convolutional Neural Networks (AR-CNNs):** Used to study systems that evolve over time and assume that the likelihood of some data depends only on what has happened in the past. It’s a useful way of looking at many systems, from weather prediction to stock prediction.

#### Generative Adversarial Networks (GANs)
- **Generative Adversarial Networks (GANs):** A machine learning model format that involves pitting two networks against each other to generate new content. The training algorithm swaps back and forth between training a generator network (responsible for producing new data) and a discriminator network (responsible for measuring how closely the generator network’s data represents the training dataset).

#### Transformer-Based Models
- **Transformer-Based Models:** Most often used to study data with some sequential structure (such as the sequence of words in a sentence). Transformer-based methods are now a common modern tool for modeling natural language.

# Generative AI with AWS DeepComposer

## What is AWS DeepComposer?

AWS DeepComposer gives you a creative and easy way to get started with machine learning (ML), specifically generative AI. It consists of a USB keyboard that connects to your computer to input melody and the AWS DeepComposer console, which includes AWS DeepComposer Music Studio to generate music, learning capsules to dive deep into generative AI models, and AWS DeepComposer Chartbusters challenges to showcase your ML skills.

### Summary

#### AWS DeepComposer Keyboard
- You don't need an AWS DeepComposer keyboard to finish this course. You can import your own MIDI file, use one of the provided sample melodies, or use the virtual keyboard in the AWS DeepComposer Music Studio.

#### AWS DeepComposer Music Studio
- To generate, create, and edit compositions with AWS DeepComposer, you use the AWS DeepComposer Music Studio. To get started, you need an input track and a trained model.
  - **Input Track:** You can use a sample track, record a custom track, or import a track.

- For the ML technique, you can use either a sample model or a custom model.
  - Each AWS DeepComposer Music Studio experience supports three different generative AI techniques:
    - **Generative Adversarial Networks (GANs):** Use to create accompaniment tracks.
    - **Autoregressive Convolutional Neural Networks (AR-CNNs):** Use to modify notes in your input track.
    - **Transformers:** Use to extend your input track by up to 30 seconds.

### Demo
- **AWS DeepComposer Demo:** [Watch the demo](https://www.youtube.com/watch?v=CFWsZ38x93k)

### Summary of Demo
- In this demo, you went through the AWS DeepComposer console where you can learn about deep learning, input your music, and train deep learning models to create new music.

### AWS DeepComposer Learning Capsules
- To learn the details behind generative AI and ML techniques used in AWS DeepComposer you can use easy-to-consume, bite-sized learning capsules in the AWS DeepComposer console.

### AWS DeepComposer Chartbusters Challenges
- **Chartbusters** is a global challenge where you can use AWS DeepComposer to create original compositions and compete in monthly challenges to showcase your machine learning and generative AI skills.

# GANs with AWS DeepComposer

## Summary

### What are GANs?

A GAN is a type of generative machine learning model which pits two neural networks against each other to generate new content: a generator and a discriminator.

- **Generator:** A neural network that learns to create new data resembling the source data on which it was trained.
- **Discriminator:** Another neural network trained to differentiate between real and synthetic data.

The generator and the discriminator are trained in alternating cycles. The generator learns to produce more and more realistic data while the discriminator iteratively gets better at learning to differentiate real data from the newly created data.

#### Collaboration between an Orchestra and Its Conductor

A simple metaphor of an orchestra and its conductor can be used to understand a GAN. The orchestra trains, practices, and tries to generate polished music, and then the conductor works with them, as both judge and coach. The conductor judges the quality of the output and at the same time provides feedback to achieve a specific style. The more they work together, the better the orchestra can perform.

The GAN models that AWS DeepComposer uses work in a similar fashion. There are two competing networks working together to learn how to generate musical compositions in distinctive styles.

- **Generator:** Produces new music as the orchestra does.
- **Discriminator:** Judges whether the music generator creates is realistic and provides feedback on how to make its data more realistic, just as a conductor provides feedback to make an orchestra sound better.

#### Training Methodology

Let’s dig one level deeper by looking at how GANs are trained and used within AWS DeepComposer. During training, the generator and discriminator work in a tight loop as depicted in the following image.

> Note: While this figure shows the generator taking input on the left, GANs in general can also generate new data without any input.

- **Generator:**
  - Takes in a batch of single-track piano rolls (melody) as the input and generates a batch of multi-track piano rolls as the output by adding accompaniments to each of the input music tracks.
  - The discriminator then takes these generated music tracks and predicts how far they deviate from the real data present in the training dataset. This deviation is called the generator loss. This feedback from the discriminator is used by the generator to incrementally get better at creating realistic output.

- **Discriminator:**
  - As the generator gets better at creating music accompaniments, it begins fooling the discriminator. So, the discriminator needs to be retrained as well. The discriminator measures the discriminator loss to evaluate how well it is differentiating between real and fake data.
  - Beginning with the discriminator on the first iteration, we alternate training these two networks until we reach some stop condition; for example, the algorithm has seen the entire dataset a certain number of times or the generator and discriminator loss reach some plateau (as shown in the following image).

### New Terms

- **Generator:** A neural network that learns to create new data resembling the source data on which it was trained.
- **Discriminator:** A neural network trained to differentiate between real and synthetic data.
- **Generator Loss:** Measures how far the output data deviates from the real data present in the training dataset.
- **Discriminator Loss:** Evaluates how well the discriminator differentiates between real and fake data.

## Summary

# AR-CNN with AWS DeepComposer

### Image-based Representation

To better understand how the AR-CNN model works, let’s first discuss how music is represented so it is machine-readable.

Nearly all machine learning algorithms operate on data as numbers or sequences of numbers. In AWS DeepComposer, the input tracks are represented as a piano roll. In each two-dimensional piano roll, time is on the horizontal axis and pitch is on the vertical axis. You might notice this representation looks similar to an image.

The AR-CNN model uses a piano roll image to represent the audio files from the dataset. You can see an example in the following image where on top is a musical score and below is a piano roll image of that same score.

### How the AR-CNN Model Works

When a note is either added or removed from your input track during inference, we call it an edit event. To train the AR-CNN model to predict when notes need to be added or removed from your input track (edit event), the model iteratively updates the input track to sound more like the training dataset. During training, the model is also challenged to detect differences between an original piano roll and a newly modified piano roll.

### New Terms

- **Piano roll:** A two-dimensional piano roll matrix that represents input tracks. Time is on the horizontal axis and pitch is on the vertical axis.
- **Edit event:** When a note is either added or removed from your input track during inference.

# Building a Custom GAN
## Build a Custom GAN Model (Optional): Part 1

To create the custom GAN, you will need to use an instance type that is not covered in the Amazon SageMaker free tier. You may incur a cost if you want to build a custom GAN.

You can learn more about SageMaker costs in the [Amazon SageMaker pricing documentation](https://aws.amazon.com/sagemaker/pricing/).

### Setting Up the AWS DeepComposer Notebook

1. Go to the [AWS Management Console](https://aws.amazon.com/console/) and search for Amazon SageMaker.
2. Once inside the SageMaker console, look to the left-hand menu and select **Notebook Instances**.
3. Next, choose **Create notebook instance**.
4. In the Notebook instance setting section, give the notebook a name, for example, `DeepComposerUdacity`.
5. Based on the kind of CPU, GPU, and memory you need, the next step is to select an instance type. For our purposes, we’ll configure an `ml.c5.4xlarge`.
6. Leave the Elastic Inference defaulted to none.
7. In the Permissions and encryption section, create a new IAM role using all of the defaults.
8. When you see that the role was created successfully, navigate down a little way to the Git repositories section.
9. Select **Clone a public Git repository to this notebook instance only**.
10. Copy and paste the public URL into the Git repository URL section: [https://github.com/aws-samples/aws-deepcomposer-samples](https://github.com/aws-samples/aws-deepcomposer-samples).
11. Select **Create notebook instance**.
12. Give SageMaker a few minutes to provision the instance and clone the Git repository.
13. When the status reads "InService," you can open the Jupyter notebook.
    ![Status is InService page](#) <!-- Replace with actual image URL -->

### Exploring the Notebook

Now that it’s configured and ready to use, let’s take a moment to investigate what’s inside the notebook.

1. Open the Notebook.
2. Click **Open Jupyter**.
3. When the notebook opens, click on "gan".
4. When the lab opens, click on `GAN.ipynb`.

#### Review: Generative Adversarial Networks (GANs)

GANs consist of two networks constantly competing with each other:

- **Generator:** A neural network that tries to generate data based on the data it was trained on.
- **Discriminator:** A neural network that is trained to differentiate between real data and data created by the generator.

### Set Up the Project

1. Run the first **Dependencies** cell to install the required packages.
2. Run the second **Dependencies** cell to import the dependencies.
3. Run the **Configuration** cell to define the configuration variables.

**Note:** While executing the cell that installs dependency packages, you may see warning messages indicating that later versions of conda are available for certain packages. It is completely OK to ignore this message. It should not affect the execution of this notebook.

4. Click **Run** or `Shift-Enter` in the cell.

### Good Coding Practices

- Do not hard-code configuration variables.
- Move configuration variables to a separate config file.
- Use code comments to allow for easy code collaboration.

### Data Preparation

The next section of the notebook is where we’ll prepare the data so it can train the generator network.

#### Why Do We Need to Prepare Data?

Data often comes from many places (like a website, IoT sensors, a hard drive, or physical paper) and it’s usually not clean or in the same format. Before you can better understand your data, you need to make sure it’s in the right format to be analyzed. Thankfully, there are library packages that can help! One such library is called [NumPy](https://numpy.org/), which was imported into our notebook.

#### Piano Roll Format

The data we are preparing today is music, and it comes formatted in what’s called a “piano roll”. Think of a piano roll as a 2D image where the X-axis represents time and the Y-axis represents the pitch value. Using music as images allows us to leverage existing techniques within the computer vision domain.

Our data is stored as a NumPy Array, or grid of values. Our dataset comprises 229 samples of 4 tracks (all tracks are piano). Each sample is a 32 time-step snippet of a song, so our dataset has a shape of:

### Model Architecture

Before we can train our model, let’s take a closer look at model architecture including how GAN networks interact with the batches of data we feed into the model, and how the networks communicate with each other.

#### How the Model Works

The model consists of two networks, a generator and a discriminator (critic). These two networks work in a tight loop:

- The generator takes in a batch of single-track piano rolls (melody) as the input and generates a batch of multi-track piano rolls as the output by adding accompaniments to each of the input music tracks.
- The discriminator evaluates the generated music tracks and predicts how far they deviate from the real data in the training dataset.
- The feedback from the discriminator is used by the generator to help it produce more realistic music the next time.
- As the generator gets better at creating better music and fooling the discriminator, the discriminator needs to be retrained by using music tracks just generated by the generator as fake inputs and an equivalent number of songs from the original dataset as the real input.
- We alternate between training these two networks until the model converges and produces realistic music.
- The discriminator is a binary classifier which means that it classifies inputs into two groups, e.g. “real” or “fake” data.

### Defining and Building Our Model

1. Run the cell that defines the generator.
2. Run the cell that builds the generator.
3. Run the cell that defines the discriminator.
4. Run the cell that builds the discriminator.

### Model Training and Loss Functions

As the model tries to identify data as “real” or “fake”, it’s going to make errors. Any prediction different than the ground truth is referred to as an error.

The measure of the error in the prediction, given a set of weights, is called a loss function. Weights represent how important an associated feature is to determining the accuracy of a prediction.

Loss functions are an important element of training a machine learning model because they are used to update the weights after every iteration of your model. Updating weights after iterations optimizes the model making the errors smaller and smaller.

### Setting Up and Running the Model Training

1. Run the cell that defines the loss functions.
2. Run the cell to set up the optimizer.
3. Run the cell to define the generator step function.
4. Run the cell to define the discriminator step function.
5. Run the cell to load the melody samples.
6. Run the cell to set the parameters for the training.
7. Run the cell to train the model.

**Training and tuning models can take a very long time – weeks or even months sometimes. Our model will take around an hour to train.**

### Model Evaluation

Now that the model has finished training it’s time to evaluate its results.
There are several evaluation metrics you can calculate for classification problems and typically these are decided in the beginning phases as you organize your workflow.

You can:

- Check to see if the losses for the networks are converging.
- Look at commonly used musical metrics of the generated sample and compare them to the training dataset.

### Evaluating Our Training Results

1. Run the cell to restore the saved checkpoint. If you don't want to wait to complete the training you can use data from a pre-trained model by setting `TRAIN = False` in the cell.
2. Run the cell to plot the losses.
3. Run the cell to plot the metrics.

### Results and Inference

Finally, we are ready to hear what the model produced and visualize the piano roll output!

Once the model is trained and producing acceptable quality, it’s time to see how it does on data it hasn’t seen. We can test the model on these unknown inputs, using the results as a proxy for performance on future data.

#### Evaluate the Generated Music

1. In the first cell, enter 0 as the iteration number.
2. Run the cell and play the music snippet.

**Example Piano Roll at Iteration 0**

1. In the first cell, enter 500 as the iteration number.
2. Run the cell and play the music snippet. Or listen to the example snippet at iteration 500. Your browser does not support the audio element.
3. In the second cell, enter 500 as the iteration number.
4. Run the cell and display the piano roll.

**Example Piano Roll at Iteration 500**

Play around with the iteration number and see how the output changes over time!

Here is an example snippet at iteration 950. Your browser does not support the audio element.

And here is the piano roll:

**Example Piano Roll at Iteration 950**

Do you see or hear a quality difference between iteration 500 and iteration 950?

#### Watch the Evolution of the Model!

Run the next cell to create a video to see how the generated piano rolls change over time.

### Inference

Now that the GAN has been trained we can run it on a custom input to generate music.

1. Run the cell to generate a new song based on "Twinkle Twinkle Little Star". Or listen to the example of the generated music here: Your browser does not support the audio element.
2. Run the next cell and play the generated music. Or listen to the example of the generated music here: Your browser does not support the audio element.

### Stop and Delete the Jupyter Notebook When You Are Finished!

This project is not covered by the AWS Free Tier so your project will continue to accrue costs as long as it is running.

Follow these steps to stop and delete the notebook:

1. Go back to the [Amazon SageMaker console](https://aws.amazon.com/console/).
2. Select the notebook and click **Actions**.
3. Select **Stop** and wait for the instance to stop.
4. Select **Delete**.

# Glossary of Terms

**Action:** For every state, an agent needs to take an action toward achieving its goal.

**Agent:** The piece of software you are training is called an agent. It makes decisions in an environment to reach a goal.

**Discriminator:** A neural network trained to differentiate between real and synthetic data.

**Discriminator loss:** Evaluates how well the discriminator differentiates between real and fake data.

**Edit event:** When a note is either added or removed from your input track during inference.

**Environment:** The environment is the surrounding area within which the agent interacts.

**Exploration versus exploitation:** An agent should exploit known information from previous experiences to achieve higher cumulative rewards, but it also needs to explore to gain new experiences that can be used in choosing the best actions in the future.

**Generator:** A neural network that learns to create new data resembling the source data on which it was trained.

**Generator loss:** Measures how far the output data deviates from the real data present in the training dataset.

**Hidden layer:** A layer that occurs between the output and input layers. Hidden layers are tailored to a specific task.

**Input layer:** The first layer in a neural network. This layer receives all data that passes through the neural network.

**Output layer:** The last layer in a neural network. This layer is where the predictions are generated based on the information captured in the hidden layers.

**Piano roll:** A two-dimensional piano roll matrix that represents input tracks. Time is on the horizontal axis and pitch is on the vertical axis.

**Reward:** Feedback is given to an agent for each action it takes in a given state. This feedback is a numerical reward.



