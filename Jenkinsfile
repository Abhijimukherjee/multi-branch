
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
	withCredentials([usernamePassword(credentialsId: WCS_DL_ENCRYPTED_CREDENTIAL_SET, usernameVariable: 'DBUSER', passwordVariable: 'DBPASS_ENCYPT')]) {
	sh """
	echo $projectName
	if [ $BUILD_NUMBER -gt 999 ]
	then
	printf $BUILD_NUMBER | tail -c 3 
	else
	printf "%03d" "$BUILD_NUMBER" 
	echo "\${printf "%03d" "$BUILD_NUMBER"}"
	fi
	#cat temp_runnum.txt
	#read -r runnum<temp_runnum.txt
	#sed -i 's%NUM%${cat temp_runnum.txt}%' PCGFinanceReports.txt > PCGFinanceReport.txt
        """
	}
	}
	}
}
}
