pipeline {
    agent any
    stages {
        stage('Build application') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
       		 	emailext (
            			subject: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
            			body: """<p>STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
              			<p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
            			to: "rahul.kumar@renovite.com",
            			replyTo: "rahul.kumar@renovite.com",
				recipientProviders: [[$class: 'DevelopersRecipientProvider']]
          		)
                }
            }
        }
    }
}
