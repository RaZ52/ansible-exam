node {
    stage('Preparation') {
        git 'https://github.com/RaZ52/ansible-exam.git'
    }
    stage('Deployment') {
        ansiblePlaybook credentialsId: 'deploy-ssh-key', inventory: 'inventory', playbook: 'distributed.yml', vaultCredentialsId: 'ansible-vault'
    }
    stage('Integration test') {
        def response = httpRequest 'http://172.17.0.6/'
        println("Status: "+response.status)
    }
}
