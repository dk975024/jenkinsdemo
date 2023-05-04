pipeline {
    agent any
    stages {
        stage(terraform) {
            steps {
                sh 'terraform init'
                sh 'terraform apply --auto-approve'
                sh 'docker build -t httpd:latest . '
                sh 'docker run -d --name httpd -p 80:80 httpd:latest'
            } 
        }
    }
}
