pipeline {
    agent any

    stages {
        stage("Checkout GIT"){
            steps{
                echo 'pulling...';
                git branch: 'main',
                url : 'https://github.com/many-ux/SpringProject.git';
            }
        }
        
        stage('Testing Maven'){
            steps{
                sh """mvn -version"""
            }
        }

        stage('Build') {
            steps {
                sonar:sonar
            }
        }

        
       stage('Test') {
        steps {
        sh 'mvn test'
        }
            /*post {
            always {
            steps {
                junit 'target/surefire-reports/*.xml'
            }
        }
            }*/
        }

        stage ('SonaQube Analysis'){
	        def mvnHome = tool name: 'maven-3', type: 'maven'
	         withSonarQubeEnv('sonar') {
		        sh "${mvHome}/bin/mvn sonar:sonar"
		    }
        }

        
    }
}

