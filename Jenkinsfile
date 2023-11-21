pipeline {
    agent any

    stages {
        stage('Build app') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Rishita-Soni/JenkinsPipeline.git']])
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    bat 'docker build -t jenkinsjavaapp .'
                }
            }
        }
        stage('Change image tag'){
            steps{
                script{
                    bat 'docker tag jenkinsjavaapp rishitasoni/jenkinsjava_app:v1.0'
                }
            }
        }
        stage('Push image to docker hub'){
            steps{
                script{
                   
                    bat 'docker login -u rishitasoni -p welcome123'
                    
                    bat 'docker push rishitasoni/jenkinsjava_app:v1.0'
                }
            }
        }
    }
}



