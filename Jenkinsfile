pipeline {
    agent any

    environment {
        NEW_VERSION ='1.0.0'
        MY_CRED = credentials('cred')
    }

    stages {
        stage("build") {
            steps {
                echo "build something"
            }
        }

        stage("test") {
            when {
                expression { env.BRANCH_NAME == 'main' || BRANCH_NAME == 'dev' }
            }
            steps {
                echo "test one"
            }
        }

        stage('deploy') {
            parallel{
                stage('deploye stage'){
                    steps{
                        echo "deploying the stage"
                    }
                }
                stage('Deploy to Prod') {
                    steps {
                        withCredentials([usernamePassword(credentialsId: 'cred', 
                                          usernameVariable: 'USERNAME', 
                                          passwordVariable: 'PASSWORD')]) {
                        sh 'echo Username: $USERNAME, Password: $PASSWORD'
                                                            }
                            }           
                }

            }
        }
    }

    post {
        always {
            echo "cleaning"
        }
    }
}
