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
                withSonarQubeEnv(installationName: 'SONAR_9.3', envOnly: true, credentialsId: 'SONAR_TOKEN') {
                    sh "/usr/local/apache-maven-3.8.6/bin/mvn clean  sonar:sonar -Dsonar.login=552df7b317f3eacb2fca289afb839d5f46ee7b06 sonar:sonar"
					echo "${env.SONAR_HOST_URL}"

                }

            }
        }
    }

}