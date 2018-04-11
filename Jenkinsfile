pipeline {
    agent any
    stages {
        stage('Build application') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
			emailext body: '''<h2 style="color: #2e6c80;">Hi,</h2>
			<h4 style="color: #2e6c80;">$DEFAULT_CONTENT</h2>
			<h2 style="color: #2e6c80;">&nbsp;</h2>
			<h2 style="color: #2e6c80;">Regards,</h2>
			<h2 style="color: #2e6c80;">Dev-OPS Team</h2>
			<p><strong>&nbsp;</strong></p>''', 
			mimeType: 'text/html',
			postsendScript: '$DEFAULT_POSTSEND_SCRIPT', presendScript: '$DEFAULT_PRESEND_SCRIPT',
			replyTo: 'rahul.kumar808@gmail.com', subject: '$DEFAULT_SUBJECT', to: 'rahul.kumar@renovite.com'
                }
            }
        }
    }
}
