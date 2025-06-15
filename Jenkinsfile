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

                sh """ echo "ST2-3366927u: Server 1 is successfully created"
                """
            }
        }

        stage('ST3-3366927u') {
            steps {
                 
                 sh 'mvn install -Dmaven.test.skip=false'
                         

                 sh """ 
                 echo "ST3-3366927u: Server 1 is healthy - Health check done"
                 """
            }
        }

        stage('ST4-Parallel-3366927u') {

            parallel {

                stage('ST4A-3366927u') {
                    steps{
                        sh """echo "ST4A-3366027u: SQLI Check Completed"
                        """
                    }
                }

                stage("ST4B-3366927u") {
                    steps {
                        sh """ echo "Hello Student, thanks for keeping up!ST4B-3366927u: XSS Check Completed"
                        """
                    }
                }

                stage('ST4C testing') {
                    steps {
                        sh "echo ${APP_ENV}"
                    }
                }
            }
        }

        stage('ST5-3366927u') {
            steps {
                    input("Continue the pipeline?")
                    sh """ echo "ST5-3366927u: Continue the pipeline"
                    """
            }
        }
        
        stage('ST6-3366927u') {
            steps {
                    sh """ echo "ST6-3366927u: Ready for next phase"
                    """
            }
        }

    }   
}
