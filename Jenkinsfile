#!/usr/bin/env groovy

pipeline {
    agent none
    stages {
        stage('Checkout on Linux') {
            agent { 
                label 'linux'
            }
            steps {
                echo 'Checkout for linux.'
                sh '''
                cd /root/bharat
                rm -rf xtractcloud
                /usr/bin/git clone git@github.com:nutanixgso/xtractcloud.git
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
                echo 'Build on windows'                
            }
            post { 
                always {
                    echo 'I am in post section'
                }
            }
        }
   }
}
