pipeline {

    agent {
        node {
            label 'master'
        }
    }

    tools { 
        maven 'maven3' 
    }

    options {
        buildDiscarder logRotator( 
                    daysToKeepStr: '15', 
                    numToKeepStr: '10'
            )
    }

    environment {
        APP_NAME = "STUDENT_APP"
        APP_ENV  = "DEV"
    }

    stages {
        
        stage('ST1-3366927u') {
            steps {
                cleanWs()
                sh """
                echo "ST1-3366927u: Setup Environment Completed"
                """
            }
        }

        stage('ST2-3366927u') {
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/spring-projects/spring-petclinic.git']]
                ])
            }
        }

        stage('ST3-3366927u') {
            steps {
                 sh 'mvn install -Dmaven.test.skip=false'
            }
        }

        stage('Environment Analysis') {

            parallel {

                stage('Printing All Global Variables') {
                    steps{
                        sh """
                        env
                        """
                    }
                }

                stage("Execute Shell") {
                    steps {
                        sh 'echo "Hello Student, thanks for keeping up!"'
                    }
                }

                stage('Print ENV variable') {
                    steps {
                        sh "echo ${APP_ENV}"
                    }
                }
            }
        }

        stage('Printing All Global Variables') {
            steps {
                sh """
                env
                """
            }
        }

    }   
}
