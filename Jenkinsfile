pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
			bat label: '', script: 'mvn -f maven-demo-docker/pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
           }
        }
		stage('Create Tomcat Docker Image'){
		steps {
               bat label: '', 'docker build . -t maven-demo-docker:1
            }
		}
    }
}

