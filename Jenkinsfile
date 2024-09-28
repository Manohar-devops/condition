pipeline {
    agent {
        label 'node-agent-slave'
    }
    environment {
        DEPLOY_TO = 'Prod' // Just an environment variable
    }
    stages {
        stage ('whenstage') {
            when {
                //environment based condition
                environment name: 'DEPLOY_TO', value: 'Prod'
            }
            steps{
                echo "Deploying Application to whenstage"
            }
        }
    }
}

// default env defined by jenkins for MBP
// this willonly execute with multi branch pipeline
pipeline {
    agent {
        label 'java-agent-slave'
    }
    stages {
        stage ('Build Stage') {
            steps {
                echo "Application building in build stage"
            }
        }
        stage ('Production Stage') {
            when {
                expression {
                    BRANCH_NAME ==~ /(production|staging)/
                    }
            }
            steps {
                echo "Application deploying in production"
            }          
        }
    }
}



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
                    environment name: 'DEPLOY_TO', value: 'Prod'
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
        stage ('allOff stage') {
            when {
                allOf {
                    environment name: 'DEPLOY_TO', value: 'prod'
                    expression {
                        BRANCH_NAME ==~ /(production|staging)/
                    }
                }
            }
            steps {
                echo "App deployed in allOf stage"
            }
        }
    }
 }



 // tag based deploymnet

 pipeline {
    agent any
    stages {
        stage ('Build') {
            steps {
                echo "Building app"
            }
        }
        stage ('Sonar') {
            steps {
                echo "code quakity"
            }
        }
        stage ('DockerImage') {
            steps {
                echo "creating docker image"
            }
        }
        stage ('DockerPush') {
            steps {
                echo "pushing docker image to docker hub"
            }
        }
        stage ('stage') {
            when {
                branch 'release/*'
            }
            steps {
                echo "Deploying app in stage"
            }
        }
        stage ('production') {
            when {
                // Application should only deploy to prod if the app is going through tag
                //v1.x.x ==> v1.2.3 is the tag version
                tag pattern: "v\\d{1,2}\\.\\d{1,2}\\.\\d{1,2}\\", comparator: "REGEXP"
            }
            steps {
                echo "Deploying app in production"
            }
        }
    }
 }
