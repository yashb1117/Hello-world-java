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
    }
}
