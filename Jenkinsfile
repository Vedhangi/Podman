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
                    bat 'docker build -t podman_image:1.2 -f Dockerfile .'
                }
            }
        }
      
        stage('Run ') {
            steps {
                script {
                    
                    bat 'docker run localhost/podman_image:1.2'
                }
            }
        }
    }
}
