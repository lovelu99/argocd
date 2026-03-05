pipeline {
    agent any
    parameters {
        string(name: 'IMAGE_TAG', description: 'Image tag to deploy')
        //string(name: 'IMAGE_TAG', description: 'Image tag to deploy', defaultValue: 'latest')
    }

    stages {
        stage('Update Deployment') {
            steps {
                echo 'update deployment...'
                // Add your build steps here
                sh 'cat ./k8s/deployment.yaml'
                sh "sed -i 's/image: noakhali\\/myapp:.*/image: noakhali\\/myapp:${params.IMAGE_TAG}/g' ./k8s/deployment.yaml"
                sh 'cat ./k8s/deployment.yaml'
            }
        }
        stage('Push to git hub') {
            steps {
                echo 'push to git hub...'
                // Add your test steps here
                sh 'git config --global user.name "Your Name"'
                sh 'git config --global user.email "your.email@example.com"'
                sh 'git checkout main'
                sh 'git add ./k8s/deployment.yaml'
                sh "git commit -m 'Update deployment with image tag ${params.IMAGE_TAG}'"
                withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'password', usernameVariable: 'username')]) {
                   // some block
                    //  sh "git push https://$username:$password@github.com/${username}/argocd.git main"
                      sh "git push https://$username:$password@github.com/${username}/argocd.git main"
                //     sh '''
                //         git push https://$username:$password@github.com/$username/argocd.git HEAD:main
                //     '''
                // }
                
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