pipeline {
    agent any

    parameters {
        booleanParam(name: "RUN_INTEGRATION_TEST", defaultValue: true)
    }

    stages {
        stage('Test') {
            parallel {
                stage('Unit tests') {
                    steps {
                        sh './mvnw test -D testGroups=unit'
                    }
                }
                stage('Integration tests') {
                    when {
                        expression { return params.RUN_INTEGRATION_TESTS }
                    }

                    steps {
                        sh './mvnw test -D testGroups=integration'
                    }
                }
            }
        }
    }
}
