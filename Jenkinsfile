pipeline {
    agent any

    environment {
        IMAGE_REPO = "jihnordraven"
        IMAGE_NAME = "test-app"
    }

    stages {
        stage("Unit test") {
            steps {
                sh "npm install"
                sh "npm run test"
            }
        }
        stage("E2e test") {
            steps {
                sh "npm run test:e2e"
            }
        }
        stage("Build image") {
            steps {
                sh "docker build -t ${IMAGE_REPO}/${IMAGE_NAME}:${BUILD_ID} ."
            }
        }
        stage("Push image") {
            steps {
                sh "docker login -u jihnordraven -p Qeadws123321%"
                sh "docker push ${IMAGE_REPO}/${IMAGE_NAME}:${BUILD_ID}"
                // withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                //     sh "docker login -u jihnordraven -p ${dockerhubpwd}"
                //     sh "docker push ${IMAGE_REPO}/${IMAGE_NAME}:${BUILD_ID}"
                // }
            }
        }
        stage("Delete image") {
            steps {
                sh "docker rmi ${IMAGE_REPO}/${IMAGE_NAME}:${BUILD_ID}"
            }
        }
        stage("Finish") {
            steps {
                echo "Finish Successfully"
            }
        }
    }
}