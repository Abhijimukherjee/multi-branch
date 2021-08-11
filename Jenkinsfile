
def allJob = JOB_NAME.tokenize('/') as String[];
def projectName = allJob[0];

node('master'){
    stage('stage1'){
def GIT_COMMIT_EMAIL = sh (returnStdout: true, script: '''if [ $BUILD_NUMBER -gt 999 ]
	then
	printf $BUILD_NUMBER | tail -c 3
	else
	printf "%03d" "$BUILD_NUMBER"
	fi''').trim()
    echo "Git committer email: ${GIT_COMMIT_EMAIL}"
    }
}

pipeline {
  agent any
  stages {
    stage('run_Finance_dataextract'){
        when {
		expression { "${projectName}" == 'Finance' }
        }
      steps {
	sh """
	touch test.txt
	echo "NUM" > test.txt
	echo $projectName
	echo "\${GIT_COMMIT_EMAIL}"
	sed -i 's%NUM%\${GIT_COMMIT_EMAIL}%' test.txt > tests.txt
        """
	}
	}
	}
}
