pipeline {
    agent any
    environment{
        dockerImage =''
        registry ='sudhanshu87/applied_project'
        registryCredential ='dockerhub_id'
        
    }

    stages {
        stage('checkout'){
            steps{
                checkout scmGit(branches: [[name: '*/master']],
                extensions: [],
                userRemoteConfigs: [[url: 'https://github.com/shashank100rabh/applied_devops_project']]
                )
            }
      
        }
        stage('Build Image'){
            steps{
                script{
                    dockerImage = docker.build registry
                }
            }
        }
        stage('Upload Image') {
            steps{    
                 script {
                    docker.withRegistry( '', registryCredential ) {
                        dockerImage.push()
                    }
                }
            }
        }
        
    }
 }
