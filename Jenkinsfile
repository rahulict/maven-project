pipeline {
    agent { label 'master' }
    stages {
        stage('Build application') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy artifect') {
            agent { label 'master' }
            steps {
                sh 'cp **/target/webapp.war /opt/test/wars/'
            }
            post {
                success {
                    sh 'ansible-playbook /home/ec2-user/ansible/deploy_app.yml'
                }
            }
        }
    }
}
