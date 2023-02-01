pipeline {
    agent any

    tools {
        maven "MY MAVEN"
    }

    stages {
        stage('checkout') {
            steps {
                echo 'github project is downloading'
                git branch: 'master' , credentialsId: 'Credential1', url: 'https://github.com/SaharMortazavi/Jenkins-Docker-project.git'
                sh 'pwd'
            }
        }
        stage('changing directory'){
            steps {
                dir('backend'){
                    sh 'pwd'
                    sh 'mvn clean'
                }
            }
        }
        stage('compile') {
            steps {
                dir('backend'){
                    echo 'start compiling...'
                    sh 'pwd'
                    sh 'mvn compile'
                    sh 'pwd'
                }
            }
        }
        stage('test-compile') {
            steps {
                dir('backend'){
                    echo 'start test-compiling...'
                    sh 'pwd'
                    sh 'mvn test-compile'
                    sh 'pwd'
                }
            }
        }
        stage('test') {
            steps {
                dir('backend'){
                    echo 'start testing...'
                    sh 'pwd'
                    sh 'mvn test'
                    sh 'pwd'
                }
            }
        }


        stage('build') {
            steps {
                dir('backend'){
                    echo 'building...'
                    sh 'pwd'
                    sh 'mvn package'
                    sh 'pwd'
                    echo 'finished building'
                }
            }
        }

        stage('deploy') {
            steps {
                dir('backend'){
                    sh 'cp ./target/ROOT.war /artifacts'
                }
            }
        }
//
//         stage('package') {
//             steps {
//                 echo 'packaging...'
//                 sh 'mvn jar:jar'
//                 echo 'packaged'
//             }
//         }
    }

}
