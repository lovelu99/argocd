pipeline {
    agent any
    parameters {
        string(name: 'IMAGE_TAG', description: 'Image tag to deploy')
        //string(name: 'IMAGE_TAG', description: 'Image tag to deploy', defaultValue: 'latest')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Add your build steps here
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // Add your test steps here
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Add your deploy steps here
            }
        }
    }
}