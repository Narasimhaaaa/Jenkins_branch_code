pipeline {
    agent any

    environment {
        BRANCH_NAME = "${env.BRANCH_NAME}"
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
            steps {
                echo "deploy"
            }
        }
    }

    post {
        always {
            echo "cleaning"
        }
    }
}
