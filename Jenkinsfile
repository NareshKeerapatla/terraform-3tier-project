pipeline {
    agent any 

    parameters {
        choice(name: 'ACTION', choices: ['apply', 'destroy'], description: 'Terraform action')
    }

    environment {
        AWS_ACCESS_KEY_ID     = credentials('AKIASTOWSBMWURUEKB42')
        AWS_SECRET_ACCESS_KEY = credentials('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')
    }

    stages {

        stage('checkout') {
            steps {
                git 'https://github.com/ReyazShaik/terraform-3tier-project.git'
            }
        }

        stage('init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('validate') {
            steps {
                sh 'terraform validate'
            }
        }

        stage('plan') {
            steps {
                sh 'terraform plan'
            }
        }

        stage('apply/destroy') {
            steps {
                sh "terraform ${ACTION} --auto-approve"
            }
        }
    }
}
