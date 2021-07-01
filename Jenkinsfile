#!/usr/bin/env groovy
// see https://jenkins.io/doc/book/pipeline/syntax/

pipeline {
    
    agent any
    
//    parameters {
        
//        booleanParam(name: "RELEASE", defaultValue: true)
//    }
    
    stages {

        stage("Build") {
            steps {
                echo 'testing build'
            }
        }
        
        stage("Publish") {
            when (BRANCH_NAME = 'feature1')
            {
            steps {
                echo 'testing publish'
            }
            }    
        }
    }
}
