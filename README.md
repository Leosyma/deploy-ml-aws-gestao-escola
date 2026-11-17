# Machine Learning Deployment on AWS for School Management

This project is a Flask web application developed to deploy a Machine Learning model for school admission prediction.

The application allows users to enter student assessment information, such as English exam score, psychotechnical exam score, and IQ score. The input data is validated, preprocessed with a saved scaler, and passed to a trained Machine Learning model to predict whether the student can be admitted to the course.

## Project Objective

The main objective of this project is to demonstrate how to deploy a Machine Learning model through a web application and prepare it for cloud deployment on AWS.

The application allows users to:

* Enter student assessment data through a web form;
* Validate input values before prediction;
* Apply preprocessing using a saved scaler;
* Generate predictions using a trained Machine Learning model;
* Display the admission result directly on the web page;
* Run the application locally or deploy it on an AWS EC2 instance.

## Technologies Used

* Python
* Flask
* Pandas
* NumPy
* Scikit-learn
* Pickle
* Gunicorn
* HTML
* AWS EC2
* Systemd

## Project Structure

```text
.
├── app.py                  # Main Flask application
├── index.html              # HTML page with the input form
├── modelo_final.pkl    # Trained Machine Learning model
├── scaler_final.pkl        # Scaler used for preprocessing
├── requirements.txt        # Project dependencies
├── LEIAME.txt              # Local and AWS deployment instructions
└── README.md               # Project documentation
```

## How the Application Works

The application follows this workflow:

1. The user accesses the home page;
2. A form is displayed with the required student information;
3. The user enters the English exam score, psychotechnical exam score, and IQ score;
4. The application validates whether the values are within the expected ranges;
5. The input data is converted into the same structure used during training;
6. The saved scaler is applied to standardize the input data;
7. The trained Machine Learning model generates the prediction;
8. The result is displayed on the web page.

## Input Features

The model uses the following input variables:

* English exam score
* Psychotechnical exam score
* IQ score

The expected value ranges are:

* English exam score: 0 to 10
* Psychotechnical exam score: 0 to 100
* IQ score: 0 to 200

## Installation

Create a Conda virtual environment:

```bash
conda create --name admissao-escolar python=3.13
```

Activate the environment:

```bash
conda activate admissao-escolar
```

Install `pip` and the project dependencies:

```bash
conda install pip
pip install -r requirements.txt
```

## Running Locally

For development mode, run:

```bash
flask run
```

For production mode with Gunicorn, run:

```bash
gunicorn -w 4 app:app
```

## AWS Deployment

This project also includes instructions for deploying the Flask application on an AWS EC2 instance.

The general deployment process includes:

1. Creating or accessing an EC2 instance;
2. Installing Miniconda and the project dependencies;
3. Running the application with Gunicorn;
4. Binding the application to a public port;
5. Optionally creating a `systemd` service to keep the application running.

Example command to run the app on AWS:

```bash
gunicorn --bind 0.0.0.0:8000 app:app
```

After deployment, the application can be accessed through the public address of the EC2 instance.

## Prediction Output

After submitting the form, the application displays one of the following results:

```text
The student can be admitted to the course
```

or

```text
The student cannot be admitted to the course
```

## Notes

* The trained model must be available as `modelo_final.pkl`.
* The scaler must be available as `scaler_final.pkl`.
* Input values must be within the expected ranges.
* The application can be executed locally or deployed on AWS using Gunicorn.
* This project was developed for educational purposes and demonstrates the deployment of a Machine Learning model in a web application.

## Author

Project developed as a practical study on Machine Learning deployment for school management using Flask and AWS.
