pipeline {
    agent { node { label 'AGENT-1' } }
    options {
        ansiColor('xterm')
    }

    stages {
        stage('Init') {
            steps {
                sh'''
                    cd terraformexample
                    ls -ltr
                    pwd
                    terraform init
                '''
            }
        }
        stage('Plan') {
            steps {
                sh'''
                    ls -ltr
                    pwd
                    cd terraformexample
                    terraform plan
                '''
            }
        }
        stage('Approve') {
            steps{
                input "Shall I apply?"
            }
        }

        stage('Apply') {
            steps{
                
                sh '''
                    pwd
                    ls -ltr
                    cd terraformexample
                    terraform apply -auto-approve
                '''
            }
        }
    }

    post { 
        always { 
            echo 'I will always run whether job is success or not'
        }
        success{
            echo 'I will run only when job is success'
        }
        failure{
            echo 'I will run when failure'
        }
    }
}