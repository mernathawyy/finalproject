pipeline {
    agent any

    stages {
        stage('Validate') {
            steps {
                sh '''
                    mvn --version
                    ansible --version
                    docker --version
                '''
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Dockerizing the app') {
            steps {
                sh '''
                    docker build -t jpetstoreapp_image .
                    docker tag jpetstoreapp_image abdalla744/jpetstoreapp_image:latest
                    docker push abdalla744/jpetstoreapp_image:latest
                '''
            }
        }
        stage('Deploy a container'){
            steps {
                sh 'ansible-playbook jpetstoreplaybook.yml'
            }
        }
    }
}
