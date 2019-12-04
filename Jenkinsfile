pipeline {
    agent any
    environment {
        PATH = "${PATH}:${getAnsiblePath()}"
    }
    stages {
        stage('checkout') {
            steps {
                checkout scm
            }
        }
      stage('Ansible version') {
       steps {
           
         sh "ansible --version"
         sh "ansible-playbook vcn.yaml --syntax-check"
         }
       }
            
        stage('Approve') {
       steps {
           
          input('Do you want to proceed?')
         }
       }
        
      stage('Ansible Deploy') {
       steps {
           
         sh "ansible-playbook vcn.yaml -vvv"
         }
       }
    }
}

def getAnsiblePath(){
def tfHome = tool name: 'ansible', type: 'org.jenkinsci.plugins.ansible.AnsibleInstallation'
 return tfHome
}
