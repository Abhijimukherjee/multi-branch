#!/usr/bin/env groovy
// see https://jenkins.io/doc/book/pipeline/syntax/

pipeline {
    
    agent any
    
    parameters {
        booleanParam(name: "RELEASE", defaultValue: false)
    }
    
    stages {

        stage("Build") {
            steps {
                echo 'testing build'
            }
        }
        
        stage("Publish") {
            when { expression { params.RELEASE } }
            steps {
                echo 'testing publish'
            }
        }
    }
}
