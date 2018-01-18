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
                        checkout([$class: 'GitSCM', branches: [[name: 'develop']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'b1e7790d-4c59-4636-9ae6-30befef7e3c0', url: 'https://github.com/bharatraut-izel/myJenkinsCode']]])
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
