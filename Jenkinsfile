pipeline {
    agent {
        image 'maven:3.6.3-adoptopenjdk-11"
        args '-v /root/.m2:/root/.m2
    }

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
                sh 'mvn -B -DskipTests clean packag'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    Junit 'target/surefire-reports/*.xml'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}

