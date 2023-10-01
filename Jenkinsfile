pipeline {
    agent any

    environment {
        registry = "316614134563.dkr.ecr.us-east-1.amazonaws.com/my-repo"
    }

    stages {
        stage("Declaretive: Npm install") {
            steps {
                echo "Start npm install"
                    script {
                        sh "npm install"
                    }
                echo "Finish npm install"
            }
        }
        stage("Declaretive: Unit test") {
            steps {
                echo "Start unit test"
                    script {
                        sh "npm run test"
                    }
                echo "Finish unit test"
            }
        }
        stage("Declaretive: E2e test") {
            steps {
                echo "Start e2e test"
                    script {
                        sh "npm run test:e2e"
                    }
                echo "Finish e2e test"
            }
        }
        stage("Declaretive: Build image") {
            steps {
                echo "Start build image"
                    script {
                        "docker build -t my-repo ."
                    }
                echo "Finish build image"
            }
        }
        stage("Tag image") {
            steps {
                echo "Start tag image"
                script {
                    sh "docker tag my-repo 316614134563.dkr.ecr.us-east-1.amazonaws.com/my-repo"
                }
                echo "Finish tag image"
            }
        }
        stage("Declaretive: Push image") {
            steps {
                echo "Start push image"
                    script {
                        sh "aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 316614134563.dkr.ecr.us-east-1.amazonaws.com"
                        sh "docker push 316614134563.dkr.ecr.us-east-1.amazonaws.com/my-repo"
                    }
                echo "Finish push image"
            }
        }
        stage("Declaretive: Kube deploy") {
            steps {
                echo "Start kube deploy"
                    withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'k8s', namespace: '', restrictKubeConfigAccess: false, serverUrl: '') {
                        sh "kubectl apply -f deployment.yaml"
                        sh "kubectl apply -f loadBalancer.yaml"
                    }
            }
        }
        stage("Declaretive: Delete image") {
            steps {
                echo "Start delete image localy"
                    script {
                        sh "docker rmi ${registry}"
                    }
                echo "Finish delete image localy"
            }
        }
        stage("Declaretive: Finish") {
            steps {
                echo "Finish CI/CD pipeline"
            }
        }
    }
}