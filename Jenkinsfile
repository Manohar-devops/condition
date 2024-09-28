//anyOf
 pipeline {
    agent {
        label 'java-agent-slave'
    }
    environment {
        DEPLOY_TO = 'abcd'
    }
    stages {
        stage ('Build stage') {
            steps {
                echo "Buildig app"
            }
        }
        stage ('anyOf stage') {
            when {
                anyOf {
                    environment name: 'DEPLOY_TO', value = 'Prod'
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
