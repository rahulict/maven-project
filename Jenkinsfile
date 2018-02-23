pipeline {
    agent { docker 'maven:3-alpine' }
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
                sh 'cp **/target/*.war /opt/test/wars/'
            }
            post {
                success {
                    sh 'ansible-playbook /home/ec2-user/ansible/deploy_app.yml'
                }
            }
        }
    }
}
