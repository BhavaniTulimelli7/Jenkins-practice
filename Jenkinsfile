pipeline {
    agent {label 'AGENT-1'}
    environment {
        PROJECT = 'EXPENSE'
        COMPONENT = 'BACKEND'
        DEPLOY_TO = 'QA'
    }
    options{
        disableConcurrentBuilds()
        timeout(time: 30,unit: 'MINUTES')
    }
    stages {
        stage('Build') {
            steps {
                script{
                    sh """
                        echo "Hello, this is build"
                        echo "Project is : $PROJECT"
                        echo "component is : $COMPONENT"
                    """
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh """
                        echo "Hello, this is test"
                    """
                }
            }
        }
        stage('Deploy') {
            when { 
                environment name: 'DEPLOY_TO', value: 'production'
            }
            steps {
                script {
                    sh """
                        echo "Hello, this is deploy"
                    """
                }
            }
        }
        stage('Parallel Stages') {
            parallel {
                stage('STAGE-1') {
                    
                    steps {
                        script{
                            sh """
                                echo "Hello, this is STAGE-1"
                                sleep 10
                            """
                        }
                    }
                }
                stage('STAGE-2') {
                    
                    steps {
                        script{
                            sh """
                                echo "Hello, this is STAGE-2"
                                sleep 10
                            """
                        }
                    }
                }
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }
        failure { 
            echo 'I will run when pipeline is failed'
        }
        success { 
            echo 'I will run when pipeline is success'
        }
    }
}