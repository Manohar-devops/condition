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
