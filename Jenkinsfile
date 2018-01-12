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
                print "Git repository is https://github.com/bharatraut-izel/myJenkinsCode.git"
                bat '''
                cd C:\\Users\\Administrator\\Desktop
                if exist myJenkinsCode rmdir myJenkinsCode /S /Q
                "C:\\Program Files\\Git\\bin\\git" clone https://github.com/bharatraut-izel/myJenkinsCode.git
                call "C:\\Program Files (x86)\\Microsoft Visual Studio 14.0\\VC\\vcvarsall.bat"
                cd C:\\Users\\Administrator\\Desktop\\myJenkinsCode\\SimpleMath\\unittest_SimpleMath
                call set.bat
                msbuild unittest_SimpleMath.vcxproj
                cd Debug
                unittest_SimpleMath.exe --gtest_output="xml:testAll.xml"
                '''
            }
            post { 
                always {
                    junit 'C:\\Users\\Administrator\\Desktop\\myJenkinsCode\\SimpleMath\\unittest_SimpleMath\\Debug\\testAll.xml'
                }
            }
        }
   }
}
