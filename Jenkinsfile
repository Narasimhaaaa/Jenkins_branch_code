pipeline {
    agent any

    environment {
        NEW_VERSION ='1.0.0'
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
                stage('deployee prod'){
                    when{
                        expression { BRANCH_NAME == 'main'}
                    }
                    steps{
                        echo 'deployee'
                        echo "${NEW_VERSION}"
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
