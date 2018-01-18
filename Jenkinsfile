#!/usr/bin/env groovy

pipeline {
    agent none
    stages {
        stage('Run Tests') {
            parallel {
                stage('Test On Windows') {
                    agent {
                        label "windows"
                    }
                    steps {
                        print "run-tests.bat"
                    }
                    post {
                        always {
                            echo 'In post of Windows'
                        }
                    }
                }
                stage('Test On Linux') {
                    agent {
                        label "linux"
                    }
                    steps {
                        echo 'run-tests.sh'
                    }
                    post {
                        always {
                            echo 'In post of linux'
                        }
                    }
                }
            }
        }
    }
}
