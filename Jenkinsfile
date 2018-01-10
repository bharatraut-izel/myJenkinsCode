#!/usr/bin/env groovy

pipeline {
    agent {
        label 'windows'
    }
    
    stages {
        stage('Checkout') {
            steps {
                print "Git repository is https://github.com/bharatraut-izel/myJenkinsCode.git"
                bat '''
                cd C:\\Users\\Administrator\\Desktop
                "C:\\Program Files\\Git\\bin\\git" clone https://github.com/bharatraut-izel/myJenkinsCode.git
                '''
            }
        }
        
        stage('Build') {
            steps {
                bat '''
                call "C:\\Program Files (x86)\\Microsoft Visual Studio 14.0\\VC\\vcvarsall.bat"
                cd C:\\Users\\Administrator\\Desktop\\myJenkinsCode\\TestApplication
                call set.bat
                msbuild TestApplication.sln
                '''
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
