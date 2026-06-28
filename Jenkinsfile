```groovy
pipeline {
    agent any

    stages {

        stage('Checkout Source Code') {
            steps {
                echo "Downloading source code..."
                checkout scm
            }
        }

        stage('Show Workspace') {
            steps {
                echo "Workspace contents:"
                sh 'pwd'
                sh 'ls -lah'
            }
        }

        stage('Run Ansible Playbooks') {
            steps {
                echo "Installing Docker..."
                sh 'ansible-playbook install-docker.yml'

                echo "Deploying Web Application..."
                sh 'ansible-playbook deploy-webapp.yml'
            }
        }

        stage('Verification') {
            steps {
                echo "Checking Docker containers..."
                sh 'docker ps'
            }
        }
    }

    post {

        success {
            echo "Pipeline completed successfully."
        }

        failure {
            echo "Pipeline failed."
        }

        always {
            echo "Pipeline execution finished."
        }
    }
}
```
