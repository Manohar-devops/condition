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
            steps {
                echo "Application deploying in production"
            }          
        }
    }
}
