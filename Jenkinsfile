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
        stage('cleaning'){
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
                }
            }
        }
        stage('test-compile') {
            steps {
                dir('backend'){
                    echo 'start test-compiling...'
                    sh 'pwd'
                    sh 'mvn test-compile'
                }
            }
        }
        stage('test') {
            steps {
                dir('backend'){
                    echo 'start testing...'
                    sh 'pwd'
                    sh 'mvn test'
                }
            }
        }


        stage('build') {
            steps {
                dir('backend'){
                    echo 'building...'
                    sh 'pwd'
                    sh 'mvn package'
                    echo 'finished building'
                }
            }
        }

        stage('deploy') {
            steps {
                dir('backend'){
                    sh 'cp ./target/ROOT.war /artifacts'
                    echo 'now war file deployed and tomcat will load it.'
                }
            }
        }

    }
    post{
        always{
            echo "pipeline is finished now and it took ${currentBuild.durationString.minus(' and counting')}."
	    junit 'target/*reports/**/*.xml'
        }
        success{
            echo 'blow your trumpets Gabriel.'
        }
        failure{
            echo 'please consider reviewing the code.'
        }
    }

}
