pipeline {
    agent any
    
    tools
    {
      maven "Maven"
    }
    
    stages {
      stage('Checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/jhawthor/CI-AnsibleJenkins.git'
             
           } 
      }

      stage('Ansible Package and Deploy') {
             
            steps {
                 
                sh "ansible-playbook ansibledeploy_main.yml -i inventories/dev/hosts --user sysadmin --key-file ~/.ssh/id_rsa"
            }
      }
    }
}