pipeline {
    agent any

    environment {
        REPOSITORY = "316614134563.dkr.ecr.us-east-1.amazonaws.com"
        IMAGE_NAME = "test-app"
        IMAGE_TAG  = "latest" 
    }

    stages {
        stage("Unit test") {
            steps {
                script {
                    sh "npm install"
                    sh "npm run test"
                }
            }
        }
        stage("E2e test") {
            steps {
                script {
                    sh "npm run e2e"
                }
            }
        }
        // stage("Build image") {
        //     steps {
        //         script {
        //             sh "docker build ${REPOSITORY}/${IMAGE_NAME}:${IMAGE_TAG}"
        //         }
        //     }
        // }
        // stage("Push image") {
        //     steps {
        //         script {
        //             withD
        //         }
        //     }
        // }
        // stage("Deploy") {}
        // stage("Delete image") {
        //     steps {
        //         script {
        //             sh "docker rmi ${REPOSIOTYR}/${IMAGE_NAME}:${IMAGE_TAG}"
        //         }
        //     }
        // }
    }
}