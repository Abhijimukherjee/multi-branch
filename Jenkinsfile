pipeline {
    agent any
    
    stages {
      stage('Build') {
            when {
            // case insensitive regular expression for truthy values
            // expression { return env.jobConfObjType = 'Pricing' }
              environment name: 'JOB_NAME', value: 'Pricing' 
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
