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
        
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }


        stage('Dockerizing the app') {
            steps {
                sh '''
                ls
                echo "0128" | sudo -S docker build -t jpetstoreapp_image .
                      
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
