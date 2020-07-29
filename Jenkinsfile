pipeline {
    agent any
    stages {
        stage('Deploy Nginx') {
            steps {
                echo 'Deploying NGINX'
                ansiblePlaybook(
                    playbook: 'nginx/nginx_install.yaml',
                    credentialsId: 'ansible_sshkey',
                    extras: '-vvvv'
                )
            }
        }
        stage('Install Parts') {
            steps {
                echo 'Installing parts to VM'
                ansiblePlaybook(
                    playbook: 'vm-docker/installingparts.yaml',
                    credentialsId: 'ansible_sshkey',
                    extras: '-vvvv'
                )
            }
        }
        stage('Deploy Docker') {
            steps {
                echo 'Deploying Docker'
                ansiblePlaybook(
                    playbook: 'vm-docker/installdocker.yaml',
                    credentialsId: 'ansible_sshkey',
                    extras: '-vvvv'
                )
            }
        }
        stage('Deploy Ghost and Traefik') {
            steps {
                echo 'Deploying Ghost and Traefik'
                ansiblePlaybook(
                    playbook: 'vm-docker/ghost.yaml',
                    credentialsId: 'ansible_sshkey',
                    extras: '-vvvv'
                )
            }
        }
        stage('Deploy Monitoring') {
            steps {
                echo 'Deploying Monitoring'
                ansiblePlaybook(
                    playbook: 'vm-docker/monitoring.yaml',
                    credentialsId: 'ansible_sshkey',
                    extras: '-vvvv'
                )
            }
        }
        stage('Deploy Logging') {
            steps {
                echo 'Deploying Logging'
                ansiblePlaybook(
                    playbook: 'vm-docker/logging.yaml',
                    credentialsId: 'ansible_sshkey',
                    extras: '-vvvv'
                )
            }
        }
    }
}