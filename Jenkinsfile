pipeline {
    agent {
        label 'node1'
    }

    parameters {
        choice(name: 'ENV', choices: ['dev', 'qa', 'prod'], description: 'Select environment')
        string(name: 'BRANCH', defaultValue: 'main', description: 'muralig')
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Deploy app?')
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: params.BRANCH,
                    url: 'https://github.com/krishna0333/spring-petclinic.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy') {
            when {
                expression { params.DEPLOY }
            }
            steps {
                echo "Deploying to ${params.ENV} environment"
            }
        }
    }
}
