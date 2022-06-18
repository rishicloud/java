pipeline {
    agent none
    stages { 
        stage('SCM Checkout') {
            agent { label 'rishi12' }
            steps{
            git url: 'https://github.com/rishicloud/java.git', branch: "main"
            }
        }

        stage('Build package') {
            agent {label 'rishi12'}
            steps{
                sh 'mvn clean package'
                }
        }

        stage('Build docker image') {
            agent { label 'rishi12' }
            steps {  
                sh 'sudo docker build -t samplespc:$BUILD_NUMBER .'
            }
        }
    }
}