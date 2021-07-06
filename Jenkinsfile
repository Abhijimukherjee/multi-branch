
// THEJOB="${JOB_NAME.substring(JOB_NAME.lastIndexOf('/') + 1, JOB_NAME.length())}"
// echo "$THEJOB"

// return ['ITEM_NAME': currentJob.getName()]

def allJob = env.JOB_NAME.tokenize('/') as String[];
def projectName = allJob[0];


pipeline {
    agent any
    
    stages {
	    stage ('configure') {
      		steps {
        	script {
		    def JOB_CONFIG=getJobConfigFromJobMetadata(JOB_NAME);
		    echo "job.config: ${JOB_CONFIG}"
			echo "${projectName}"
		}
		}
	    }
        stage('speak') {
        when {
		expression { "${projectName}" == 'Pricing' }
        }
    parallel {
        //want this and anything that modifies to run always so that deltas as well as dataloads compute correctly
        stage ('underspeak') {
          steps {
			script {
			sh """
			if( "$projectName" != 'Pricing') {
			echo 'not pricing'
			}else{
			echo ' pricing'
			}
			"""
            //rolls up attributes from child up to parent and marks what kind of children were rolled up
            echo 'this is underspeak'
          }
		 }
        }
      }
    }
	stage ('testing') {
	    steps {
            script {
		    if( "$projectName" != 'Pricing') {
		echo 'this is working'
		}
		else {
			echo 'this is not working'
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
