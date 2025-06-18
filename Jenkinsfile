pipeline {

    agent {
        docker { image 'svr-image-3366927u' }
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
                cd .
                echo "ST1-3366927u: Setup Environment Completed"
                """
            }
        }

        stage('ST2-3366927u') {
            steps {    
                script {
                    //docker run -d -p 32700:32700 --name registry registry:2
                    docker pull 'svr-image-3366927u'
                    //docker tag 'svr-image-3366927u' localhost:32700/svr-image-3366927u
                    //docker push localhost:32700/svr-image-3366927u
                    
                    docker.build('svr-image-3366927u')
                    docker.image('my-docker-image').run('-d -p 32700:80 --name my-container')
                }

                sh """ echo "ST2-3366927u: Server 1 is successfully created"
                """
            }
        }

        stage('ST3-3366927u') {
            steps {
                 
                 //sh 'mvn install -Dmaven.test.skip=false'
                         

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
