node("ansible_docker"){
    stage("Git checkout"){
        git credentialsId: 'github_cred', url: 'git@github.com:Ecriptor/example-playbook.git'
    }
    stage("Install ssh key"){
        sh 'ansible-vault decrypt secret --vault-password-file vault_pass'
        sh 'mkdir -p ~/.ssh/ && mv ./secret ~/.ssh/id_rsa && chmod 400 ~/.ssh/id_rsa'
    }    
    stage("Run playbook"){
        sh 'ansible-galaxy install -r requirements.yml'
        sh 'ansible-playbook site.yml -i inventory/prod.yml'      
    }
}
