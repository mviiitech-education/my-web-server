# My Web App

This is a simple Flask web application.

## Prerequisites

- Python 3.x
- Flask
- unittest

## Setup

1. Clone the repository:

   ```sh
   git clone https://github.com/your-repo/my-web-app.git
   cd my-web-app
   ```

2. Install the required packages:
   ```sh
   pip install -r requirements.txt
   ```

## Running the Application

To run the Flask application:

```sh
python app.py
```

## Running Tests

To run the unit tests:

```sh
python -m unittest discover
```

## Jenkins Pipeline

To set up a Jenkins pipeline for this project, follow these steps:

1. **Create a Jenkins Job**:

   - Open Jenkins and create a new pipeline job.

2. **Configure the Pipeline**:

   - In the pipeline configuration, set the pipeline script to the following:

   ```groovy
   pipeline {
       agent any

       stages {
           stage('Clone Repository') {
               steps {
                   git 'https://github.com/your-repo/my-web-app.git'
               }
           }
           stage('Install Dependencies') {
               steps {
                   sh 'pip install -r requirements.txt'
               }
           }
           stage('Run Tests') {
               steps {
                   sh 'python -m unittest discover'
               }
           }
           stage('Run Application') {
               steps {
                   sh 'nohup python app.py &'
               }
           }
       }
   }
   ```

3. **Save and Build**:
   - Save the pipeline configuration and trigger a build.

This pipeline will clone the repository, install dependencies, run tests, and start the Flask application.
