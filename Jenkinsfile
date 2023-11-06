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
    }
}

