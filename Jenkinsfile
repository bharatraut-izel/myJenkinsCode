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
