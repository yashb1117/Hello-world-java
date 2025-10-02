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
        stage ('docker image container run'){
            steps {
                echo 'docker container is running'
                sh 'docker run -d -p 8080:8080 --name c1 app'
            }
        }
    }
}
