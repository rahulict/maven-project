pipeline {
    agent any
    stages {
        stage('Build application') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
			emailext body: '', recipientProviders: [requestor()], 
			replyTo: 'Dev-OPS@doNotReply', subject: '$DEFAULT_SUBJECT', to: 'rahul.kumar@renovite.com'
                }
            }
        }
    }
}
