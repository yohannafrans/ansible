pipeline {
    agent any
    stages {
        stage('Deploy Nginx') {
            steps {
                echo 'Deploying NGINX'
                ansiblePlaybook(
                    playbook: '/root/ansible/nginx/nginx_install.yaml'
                )
            }
        }
        stage('Install Parts') {
            steps {
                echo 'Installing parts to VM'
                ansiblePlaybook(
                    playbook: '/root/ansible/vm-docker/installingparts.yaml'
                )
            }
        }
        stage('Deploy Docker') {
            steps {
                echo 'Deploying Docker'
                ansiblePlaybook(
                    playbook: '/root/ansible/vm-docker/installdocker.yaml'
                )
            }
        }
        stage('Deploy Ghost and Traefik') {
            steps {
                echo 'Deploying Ghost and Traefik'
                ansiblePlaybook(
                    playbook: '/root/ansible/vm-docker/ghost.yaml'
                )
            }
        }
        stage('Deploy Monitoring') {
            steps {
                echo 'Deploying Monitoring'
                ansiblePlaybook(
                    playbook: '/root/ansible/vm-docker/monitoring.yaml'
                )
            }
        }
        stage('Deploy Logging') {
            steps {
                echo 'Deploying Logging'
                ansiblePlaybook(
                    playbook: '/root/ansible/vm-docker/logging.yaml'
                )
            }
        }
    }
}