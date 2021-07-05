
 THEJOB="${JOB_NAME.substring(JOB_NAME.lastIndexOf('/') + 1, JOB_NAME.length())}"
 echo "$THEJOB"

// return ['ITEM_NAME': currentJob.getName()]

pipeline {
    agent any
    parameters {
        choice(
            choices: ['Pricing' , 'Product'],
            description: '',
            name: 'REQUESTED_ACTION')
    }

    stages {
        // for all other projects
        return project.displayName
		}
        stage ('Speak') {
            when {
                // Only say hello if a "greeting" is requested
                expression { params.REQUESTED_ACTION == 'Product' }
            }
            steps {
		env.JOB_BASE_NAME
                echo "Hello, bitwiseman!"
            }
        }
    }
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
