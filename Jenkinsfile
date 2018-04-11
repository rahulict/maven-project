pipeline {
    agent any
    stages {
        stage('Build application') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
    			def mailRecipients = "rahul.kumar@renovite.com"
    			def jobName = currentBuild.fullDisplayName

        		mimeType: 'text/html',
        		subject: "[Jenkins] ${jobName}",
        		to: "${mailRecipients}",
        		replyTo: "rahul.kumar@renovite.com",
        		recipientProviders: [[$class: 'CulpritsRecipientProvider']]
                }
            }
        }
    }
}
