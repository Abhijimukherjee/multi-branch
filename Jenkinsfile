pipeline {
    agent any
    
    stages {
      stage('Build') {
            if(jobName ==~ /(.*)Pricing(.*)/ ){
            // case insensitive regular expression for truthy values
            // expression { return env.jobConfObjType = 'Pricing' 
            steps {
                echo 'this should come only if job name is pricing'
            }}
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
