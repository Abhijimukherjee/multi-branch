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
                // Only say hello if a "greeting" is requested
                expression { params.REQUESTED_ACTION == 'Pricing' }
            }
            steps {
                echo "Hello, bitwiseman!"
            }
        }
    }
}
