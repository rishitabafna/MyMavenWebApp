pipeline{
	agent any
	tools{
		maven 'Maven'
	}
	stages{
		stage('a'){
			steps{
				git branch:'master', url:'https://github.com/rishitabafna/MyMavenWebApp.git'
			}
		}
		stage('b'){
			steps{
				sh 'mvn clean package'
			}
		}
		stage('Archive') {
            		steps {
                		archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            		}
        	}
        	stage('Deploy') {
            		steps {
                  		sh 'mvn clean package'
               			ansiblePlaybook playbook: 'ansible/deploy.yml', inventory: 'ansible/hosts.ini'
          
            		}
        	}
	}
}
