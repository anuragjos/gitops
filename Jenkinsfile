pipeline{
    agent any
    environment {
        DOCKERHUB_USERNAME = "anuragjoshi01"
        APP_NAME = "gitops-demo-app"
        IMAGE_TAG = "${BUILD_NUMBER}"
        IMAGE_NAME = "${DOCKERHUB_USERNAME}" + "/" + "${APP_NAME}"
        REGISTRY_CREDS = 'dockerhub'
    }
    stages{
        stage("Cleanup Workspace"){
            steps{
                script{
                    cleanWs()
                }
            }
        }
        stage("Checkout from SCM"){
            steps{
                script{
                    git credentialsId: 'github', 
                        url: 'https://github.com/anuragjos/gitops.git',
                        branch: 'master'
                }
            }
        }
        stage('Build Docker Image'){
            steps{
                script{
                    docker_image = docker.build "${IMAGE_NAME}"
                }
            }
        }
    }
}