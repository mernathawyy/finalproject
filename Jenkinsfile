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
                sh 'echo "0128" | sudo -S docker build -t jpetstoreapp_image .'
            }
        }
        stage('Deploy a container'){
            steps {
                sh 'echo "0128" | sudo -Sansible-playbook jpetstoreplaybook.yml'
            }
        }
    }
}
