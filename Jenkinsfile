pipeline {
    agent any
    stages {
        stage(terraform) {
            steps {
                sh 'terraform init'
                sh 'terraform apply --auto-approve'
                sh 'rm -rf jenkinsdemo'
                sh 'git clone https://github.com/dk975024/jenkinsdemo.git'
                sh 'cd jenkinsdemo'
                sh 'sudo su'
                sh 'docker build -t httpd:latest . '
                sh 'docker run -d --name httpd -p 80:80 httpd:latest'
            } 
        }
    }
}
