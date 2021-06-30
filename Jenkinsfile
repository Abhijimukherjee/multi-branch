def getJobConfigFromJobMetadata(jobName) {
  def jobConfig = [:];

  if(jobName ==~ /(.*)(Product|product)(.*)/ ){
    jobConfig['params.object.type']="Product"
  }else if(jobName ==~ /(.*)(Color|color)(.*)/ ){
    jobConfig['params.object.type']="Color"
  }else if(jobName ==~ /(.*)(Pricing|pricing)(.*)/ ){
    jobConfig['params.object.type']="Pricing"
  }else{
    jobConfig['params.object.type'] = "TYPE NOT RECOGNIZED!"
    throw new Exception("unable to detect job config from ${jobName}")
  }

  return jobConfig;
}

pipeline {
    agent any
    
    stages {
        stage('Build') {
            def JOB_CONFIG=getJobConfigFromJobMetadata(JOB_NAME);
            def jobConfObjType = JOB_CONFIG['params.object.type']
            when {
            // case insensitive regular expression for truthy values
            expression { return ${jobConfObjType} == 'Pricing' }
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
