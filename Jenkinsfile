pipeline {
    agent any
    tools {
        jdk 'java11'
        maven 'maven'
    }

    stages {
        stage('Code Cloning') {
            steps {
                git branch: 'main', url: 'https://github.com/yashb1117/Hello-world-java.git'
            }
        }
        stage ('maven build') {
            steps {          
                sh 'mvn clean package'
            }
        }
        stage ('maven integration test') {
            steps {
                sh 'mvn verify'
            }
        }
        stage ('docker image build'){
            steps {
                echo 'docker image is built'
                sh 'docker build -t app .'
            }
        }
        stage ('pushing docker image to docker hub'){
            steps {
              withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'dockerhubpass' , usernameVariable: 'dockerhubuser')]){
                sh ' docker login -u $dockerhubuser -p $dockerhubpass'
                sh 'docker tag app $dockerhubuser/app:latest'
                sh 'docker push $dockerhubuser/app:latest'
              }
            }
        }
    }
}
