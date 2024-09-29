pipeline {
    agent any
    parameters {
        string(name: 'CHANGE_TICKET', defaultValue: 'CH12345', description: 'Enter you change ticket')
        booleanParam(name: 'IS SRE APPROVED ?', defaultValue: 'true', description: 'Take the approval from SRE')
        choice(choices: 'Regular\nHotfix', description: 'What release is this', name: 'RELEASE')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'A secret password')
    }
    stages {
        stage ('Deploy to Dev') {
            steps {
                echo " Deployed to dev successfully"
            }
        }
        stage ('Deploy to prod') {
            steps {
                echo "Your change ticket is ${params.CHANGE_TICKET}"
                echo "This is a ${params.RELEASE}"
                echo "The password is ${params.PASSWORD}"
            }
        }
    }
}
