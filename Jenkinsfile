pipeline { 
    agent {
        node {
            label 'workstation'
        }
    }


parameters { 
choice(name: 'env', choices: ['dev', 'prod'], description: 'choose environment')
 string(name: 'component_name', defaultValue: '', description: 'component name') 
 }

stages {

    stage('Ansible') {
        steps {
            sh 'ansible-playbook -i ${component}-${env}.robog.store, roboshop.yml -e ansible_user=centos -e ansible-password=DevOps321 -e env=${env} -e role_name=${component}'
        }
    }

}

post { 
     always {
        cleanWs()
     }
}
}