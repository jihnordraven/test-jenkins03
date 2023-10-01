pipeline {
    agent any

    environment {
        registry = "316614134563.dkr.ecr.us-east-1.amazonaws.com/my-repo"
    }

    stages {
        stage("Npm install") {
            steps {
                echo "Start npm install"
                script {
                    sh "npm install"
                }
                echo "Finish npm install"
            }
        }
        stage("Unit test") {
            steps {
                echo "Start unit test"
                script {
                    sh "npm run test"
                }
                echo "Finish unit test"
            }
        }
        stage("E2e test") {
            steps {
                echo "Start e2e test"
                script {
                    sh "npm run test:e2e"
                }
                echo "Finish e2e test"
            }
        }
        stage("Build image") {
            steps {
                echo "Start build image"
                script {
                    docker.build registry
                }
                echo "Finish build image"
            }
        }
        // stage("Push image") {
        //     steps {
        //         echo "Start push image"
        //         script {

        //         }
        //         echo "Finish push image"
        //     }
        // }
        // stage("Deploy to kubernetes") {
        //     steps {
        //         echo "Start deploy to kubernetes"
        //         script {

        //         }
        //         echo "Finish deploy to kubernetes"
        //     }
        // }
        // stage("Delete image localy") {
        //     steps {
        //         echo "Start delete image localy"

        //         echo "Finish delete image localy"
        //     }
        // }
        // stage("Finish") {
        //     steps {
        //         echo "Finish CI/CD pipeline"
        //     }
        // }
    }
}