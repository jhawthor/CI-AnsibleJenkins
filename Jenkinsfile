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
        
      stage('Tools Init') {
            steps {
                script {
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                    def tfHome = tool name: 'Ansible'
                    env.PATH = "${tfHome}:${env.PATH}"
                    sh 'ansible --version'
                }
            }
      }
        
      stage('Ansible Package and Deploy') {
             
            steps {
                 
                sh "ansible-playbook ansibledeploy_main.yml -i inventories/dev/hosts --user sysadmin --key-file ~/.ssh/id_rsa"
            }
      }
    }
}