node("cd") {
    stage('Preparation') {
        git 'https://github.com/RaZ52/ansible-exam.git'
    }
    stage('Deployment') {
        ansiblePlaybook credentialsId: 'agent2-root', inventory: 'inventory', playbook: 'single.yml', vaultCredentialsId: 'vault-pass'
    }
    stage('Integration test') {
        def response = httpRequest 'http://172.17.0.5:80/'
        println("Status: "+response.status)
    }
}
