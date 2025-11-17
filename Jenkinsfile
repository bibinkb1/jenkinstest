pipeline {
    agent { label 'Agent-1' }  // use your actual agent label

    triggers {
        githubPush()    // webhook trigger
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/bibinkb1/jenkinstest.git'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                sudo rm -rf /var/www/html/*
                sudo cp -r * /var/www/html/
                sudo systemctl restart apache2 || sudo systemctl restart httpd
                '''
            }
        }
    }
}

