
def allJob = JOB_NAME.tokenize('/') as String[];
def projectName = allJob[1];

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
	printf $BUILD_NUMBER | tail -c 3
	else
	printf "%03d" "$BUILD_NUMBER"
	fi
	#sed -i 's%NUM%\${printf "%03d" "$BUILD_NUMBER"}%' test.txt > tests.txt
        """
	}
	}
	}
}
