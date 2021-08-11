
def allJob = JOB_NAME.tokenize('/') as String[];
def projectName = allJob[0];

pipeline {
  agent any
  stages {
    stage('run_Finance_dataextract'){
        when {
		expression { "${projectName}" == 'Finance' }
        }
      steps {
	sh """
	echo "NUM" > cat test.txt
	echo $projectName
	#!/bin/bash
	if [ $BUILD_NUMBER -gt 999 ]
	then
	foo=$(printf $BUILD_NUMBER | tail -c 3)
	echo "${foo}"
	else
	fi
	sed -i 's%NUM%\${foo}%' test.txt > tests.txt
        """
	}
	}
	}
}
