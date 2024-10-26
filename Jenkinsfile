pipeline {
    agent any
    
    environment {
        PATH = "C:\\Program Files\\Docker\\Docker\\resources\\bin;${env.PATH}" 
      
    }
    
    stages {
        stage('Clean and Clone Repository') {
            steps {
                cleanWs()
                bat 'git clone https://github.com/Vedhangi/Podman.git'
            }
        }
        
        stage('List Files') {
            steps {
                dir('Podman') {
                    bat 'dir'
                }
            }
        }
        
        stage('Build') {
            steps {
                dir('Podman') {
                    bat 'podman build -t podman_image:1.2 -f Dockerfile .'
                }
            }
        }

         stage('Pod Create ') {
            steps {
                script {
                    bat 'podman pod create --name mypod'
                }
            }
        }

         stage('Add container to existing pod ') {
            steps {
                script {
                    bat 'podman run -d --pod mypod podman_image:1.2'
                }
            }
        }
      
        stage('Run ') {
            steps {
                script {
                    
                    bat 'podman run localhost/podman_image:1.2'
                }
            }
        }
     
    }
}
