
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
	n=$BUILD_NUMBER
	if [ $BUILD_NUMBER -gt 999 ]
	then
	printf $BUILD_NUMBER | tail -c 3
	else
	n='printf %03d $n'
	fi
	sed -i 's%NUM%\$n%' test.txt > tests.txt
        """
	}
	}
	}
}
