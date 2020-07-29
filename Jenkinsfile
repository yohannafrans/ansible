pipeline {
    agent any
    stages {
        stage('Deploy Nginx') {
            steps {
                echo 'Deploying NGINX'
                ansiblePlaybook(
                    playbook: 'nginx/nginx_install.yaml'
                    extras: "--private-key /root/.ssh/id_rsa"
                )
            }
        }
        stage('Install Parts') {
            steps {
                echo 'Installing parts to VM'
                ansiblePlaybook(
                    playbook: 'vm-docker/installingparts.yaml'
                    extras: "--private-key /root/.ssh/id_rsa"
                )
            }
        }
        stage('Deploy Docker') {
            steps {
                echo 'Deploying Docker'
                ansiblePlaybook(
                    playbook: 'vm-docker/installdocker.yaml'
                    extras: "--private-key /root/.ssh/id_rsa"
                )
            }
        }
        stage('Deploy Ghost and Traefik') {
            steps {
                echo 'Deploying Ghost and Traefik'
                ansiblePlaybook(
                    playbook: 'vm-docker/ghost.yaml'
                    extras: "--private-key /root/.ssh/id_rsa"
                )
            }
        }
        stage('Deploy Monitoring') {
            steps {
                echo 'Deploying Monitoring'
                ansiblePlaybook(
                    playbook: 'vm-docker/monitoring.yaml'
                    extras: "--private-key /root/.ssh/id_rsa"
                )
            }
        }
        stage('Deploy Logging') {
            steps {
                echo 'Deploying Logging'
                ansiblePlaybook(
                    playbook: 'vm-docker/logging.yaml'
                    extras: "--private-key /root/.ssh/id_rsa"
                )
            }
        }
    }
}