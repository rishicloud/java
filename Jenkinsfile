pipeline {
    agent { label 'rishi12' }
    triggers { 
        cron('45 23 * * 1-5')
        pollSCM('*/5 * * * *')
    }

    stages {
        stage('scm') {
            steps {

                git url: 'https://github.com/rishicloud/java.git', branch: 'main'
            }
        }

        stage('build') {
            steps {
               
                    sh "mvn clean package"                                  
                }
            }
        }
}