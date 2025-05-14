pipeline{
    agent any
        enviroment{
            BRANCH_NAME ="${evn.BRANCH_NAME}"
        }
        stages{
            stage("build"){
                step{
                    echo"build some thing"
                }
            }

            stage("test"){
                when{
                    expression ${env.BRANCH_NAME == 'main'}
                }
                step{
                    echo "test one"
                }
            }

            stage('deploy'){
                step{
                    echo "deployeee"
                }
            }
        }
        post{
            always{
                echo "cleaning"
            }
        }
}