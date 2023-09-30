pipeline {
    agent any

    environment {
        REPOSITORY = "316614134563.dkr.ecr.us-east-1.amazonaws.com"
        IMAGE_NAME = "test-app"
        IMAGE_TAG  = "latest" 
    }

    stages {
        stage("Hello") {
            steps {
                echo "Hello World"
            }
        }
    }
}