
// THEJOB="${JOB_NAME.substring(JOB_NAME.lastIndexOf('/') + 1, JOB_NAME.length())}"
// echo "$THEJOB"

// return ['ITEM_NAME': currentJob.getName()]

def allJob = env.JOB_NAME.tokenize('/') as String[];
def projectName = allJob[0];

pipeline {
    agent any
    parameters {
        choice(
            choices: ['Pricing' , 'Product'],
            description: '',
            name: 'REQUESTED_ACTION')
    }

    stages {
        stage ('Speak') {
            when {
		expression { "${env.JOB_NAME}" == 'Pricing/branch1' }
		// echo "$env.JOB_NAME"
                // Only say hello if a "greeting" is requested
               // expression { params.REQUESTED_ACTION == 'Product' }
            }
            steps {
		    echo "${env.JOB_BASE_NAME}"
            }
        }
	stage ('testing') {
	    steps {
            script {
		if(env.JOB_NAME != 'Pricing/branch1'){
		echo 'this is working'
		}
		else {
			echo '${env.projectName}'
		}
		}
		}
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
