pipeline {
    agent any

    stages {
        stage('Validate') {
            steps {
                sh '''
                    mvn --version
                    ansible --version
                '''
            }
        }

        stage('Dockerizing the app') {
            steps {
                sh 'docker build --privileged -t jpetstoreapp_image .'
            }
        }
        stage('Deploy a container'){
            steps {
                sh 'ansible-playbook jpetstoreplaybook.yml'
            }
        }
    }
}
