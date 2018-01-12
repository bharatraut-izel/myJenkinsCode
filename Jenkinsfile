#!/usr/bin/env groovy

pipeline {
    agent none
    stages {
        stage('Checkout on Linux') {
            steps {
                echo 'Checkout for linux.'
                sh '''
                cd /root/bharat
                /usr/bin/git clone https://github.com/nutanixgso/xtractcloud.git
                '''
            }
        }
        stage('Checkout on Windows') {
            steps {
                echo 'Checkout for windows.'
            }
        }
        stage('Build on Linux') {
            agent { 
                label 'linux'
            }
            steps {
                echo 'Build on linux'
                sh '''
                cd /root/bharat/xtractcloud/linux/driver
                make
                '''
            }
        }
        stage('Build on Windows') {
            agent {
                label 'windows'
            }
            steps {
                print "Git repository is https://github.com/bharatraut-izel/myJenkinsCode.git"
                bat '''
                cd C:\\Users\\Administrator\\Desktop
                if exist myJenkinsCode rmdir myJenkinsCode /S /Q
                "C:\\Program Files\\Git\\bin\\git" clone https://github.com/bharatraut-izel/myJenkinsCode.git
                '''
            }
        }
    }
    post { 
        always { 
            echo 'I will say Hello for POST actions.'
        }
    }
}
