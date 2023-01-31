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

//         stage('test') {
//             steps {
//                 echo 'starting test.....'
//                 sh 'mvn surefire:test'
//                 echo 'finished test'
//             }
//         }
//
//         stage('package') {
//             steps {
//                 echo 'packaging...'
//                 sh 'mvn jar:jar'
//                 echo 'packaged'
//             }
//         }
    }

//     post {
//         always {
//             echo 'generating test report....'
//             junit 'target/*reports/**/*.xml'
//             echo 'test report generated'
//         }
//     }
}
