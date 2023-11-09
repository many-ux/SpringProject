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

        stage ('MVN SONARQUBE'){
    	tools {
        // Specify the Maven version here.
        maven 'M2_HOME'
    	}
    	steps {
        withSonarQubeEnv('sonar') {
            // Just call 'mvn', Jenkins knows where to find it from the 'tools' block.
            sh 'mvn sonar:sonar'
        }
    }
}
        
        stage('Nexus') {
    steps {
        sh 'mvn deploy -DskipTests'
        //checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'GIT-REPO', url: 'https://github.com/many-ux/SpringProject.git']]])
    }
}

    }
}

