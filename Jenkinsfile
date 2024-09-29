pipeline {
    agent any
    parameters {
        string(name: 'PERSON', defaultValue: 'Manohar', description: 'Enter you name')
    }
    stages {
        stage ("parameter example") {
            steps {
                echo "Welcome ${params.PERSON}" //${params.key}
            }
        }
    }
}
