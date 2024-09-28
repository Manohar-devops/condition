 //allOf
 pipeline {
    agent {
        label 'java-agent-slave'
    }
    environment {
        DEPLOY_TO = 'prod'
    }
    stages {
        stage ('Build stage') {
            steps {
                echo "Buildig app"
            }
        }
        stage ('anyOf stage') {
            when {
                allOf {
                    environment name: 'DEPLOY_TO', value: 'prod'
                    expression {
                        BRANCH_NAME ==~ /(production|staging)/
                    }
                }
            }
            steps {
                echo "App deployed in anyOf stage"
            }
        }
    }
 }
