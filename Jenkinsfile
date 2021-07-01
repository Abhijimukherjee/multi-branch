pipeline {
    agent any
    
    stages {
      stage('Build') {
            when {
        expression {
            return env.BRANCH_NAME = 'feature1';
                    }
                 } 
            steps {
                echo 'this should come only if job name is pricing'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
