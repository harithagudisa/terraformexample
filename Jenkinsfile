pipeline {
    agent { node { label 'AGENT' } }

    stages {
        stage('Init') {
            steps {
                sh'''
                    terraform Init
                '''    
            }
        }
        stage('Plan') {
            steps {
                sh'''
                    terraform plan
                '''    
            }
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
