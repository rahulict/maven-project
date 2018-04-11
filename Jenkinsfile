pipeline {
    agent any
    stages {
        stage('Build application') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
			emailext body: 'This is a test mail.', replyTo: 'rahul.kumar808@gmail.com', subject: '$DEFAULT_SUBJECT', to: 'rahul.kumar@renovite.com'
                }
            }
        }
    }
}
