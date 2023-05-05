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
                sh 'aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 260710909108.dkr.ecr.us-east-2.amazonaws.com'
                sh 'docker build -t docker .'
                sh 'docker tag docker:latest 260710909108.dkr.ecr.us-east-2.amazonaws.com/docker:latest'
                sh 'docker push 260710909108.dkr.ecr.us-east-2.amazonaws.com/docker:latest'
                #sh 'docker build -t httpd:latest . '
                #sh 'docker run -d --name httpd -p 80:80 httpd:latest'
            } 
        }
    }
}
