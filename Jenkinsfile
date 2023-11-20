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
        stage('Push image to docker hub'){
            steps{
                script{
                    withCredentials([string(credentialsId: 'dockerhubpwd1', variable: 'dockerhubpwd1')]) {
                    bat 'docker login -u rishitasoni -p ${dockerhubpwd1}'
                    }
                    bat 'docker push jenkinsjavaapp'
                }
            }
        }
    }
}



