pipeline {
    agent any
    stages {
        stage('Deploy Nginx') {
            steps {
                echo 'Deploying NGINX'
                ansiblePlaybook(
                    playbook: 'nginx/nginx_install.yaml'
                )
            }
        }
        stage('Install Parts') {
            steps {
                echo 'Installing parts to VM'
                ansiblePlaybook(
                    playbook: 'vm-docker/installingparts.yaml'
                )
            }
        }
        stage('Deploy Docker') {
            steps {
                echo 'Deploying Docker'
                ansiblePlaybook(
                    playbook: 'vm-docker/installdocker.yaml'
                )
            }
        }
        stage('Deploy Ghost and Traefik') {
            steps {
                echo 'Deploying Ghost and Traefik'
                ansiblePlaybook(
                    playbook: 'vm-docker/ghost.yaml'
                )
            }
        }
        stage('Deploy Monitoring') {
            steps {
                echo 'Deploying Monitoring'
                ansiblePlaybook(
                    playbook: 'vm-docker/monitoring.yaml'
                )
            }
        }
        stage('Deploy Logging') {
            steps {
                echo 'Deploying Logging'
                ansiblePlaybook(
                    playbook: 'vm-docker/logging.yaml'
                )
            }
        }
    }
}