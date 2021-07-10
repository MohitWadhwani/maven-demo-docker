pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
			bat label: '', script: 'mvn -f java-tomcat-sample/pom.xml clean package'
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
               sh 'docker build . -t java-tomcat-sample-docker:${env.BUILD_ID}'
            }
		}
    }
}

