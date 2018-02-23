pipeline {
    agent none
    stages {
        stage('Build application') {
    	    agent { docker 'maven:3-alpine' }
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
		step([$class: 'CopyArtifact',
		fingerprintArtifacts: true, filter: '**/target/*.war',
		flatten: true,
		projectName: 'DeployTestApp',
		selector: [$class: 'SpecificBuildSelector', buildNumber: '${BUILD_NUMBER}'], 
		target: '/opt/test/wars/'])
            }
            post {
                success {
                    sh "ansible-playbook -i /home/ec2-user/ansible/inventory/ec2.py /home/ec2-user/ansible/deploy_app.yml"
                }
            }
        }
    }
}
