pipeline {
    agent any
    tools {
        JDK 'java11'
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
                dir ('/var/lib/jenkins/workspace/Pipeline2')
                sh 'mvn clean package'
            }
        }
        stage ('maven integration test') {
            steps {
                dir ('/var/lib/jenkins/workspace/Pipeline2')
                sh 'mvn verify'
            }
        }
    }
}
