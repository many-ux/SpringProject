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
                sh 'mvn -B -DskipTests clean package'
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

        stage('MVN SONARQUBE'){
        steps{
        withSonarQubeEnv('My SonarQube Server') {
            sh 'mvn clean package sonar:sonar'
        }
    }
}

        
    }
}

