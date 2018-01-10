#!/usr/bin/env groovy

pipeline {
    agent {
        label 'windows'
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Git repository is https://github.com/bharatraut-izel/myJenkinsCode.git'
                bat '''
                cd C:\\Users\\Administrator\\Desktop
                "C:\\Program Files\\Git\\bin\\git" clone https://github.com/bharatraut-izel/myJenkinsCode.git
                '''
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building....'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
