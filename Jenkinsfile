#!/usr/bin/env groovy
// see https://jenkins.io/doc/book/pipeline/syntax/

pipeline {
        agent any
        environment {
           ENV_NAME = getEnvName(env.JOB_NAME)
        }
        stages {

        stage("Build") {
            steps {
                echo 'testing build'
            }
        }
        
        stage("Pricing") {
            when { 
                    expression { 
                                return env.ENV_NAME ;
                              }
                 }
            {
            steps {
                echo 'testing pricing'
            }
            }    
        }
    }
    }

def getEnvName(jobname) {
    if("Pricing".equals(jobname)) {
        return "true";
    } else if ("Product".equals(jobname)) {
        return "false";
    } else {
        return "false";
    }
}
