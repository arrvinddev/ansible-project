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
            sh 'aws ec2 describe-instances --filters Name=tag:Name,Values=cart-prod Name=instance-state-name,Values=running --query \ 'Reservations[*].Instances[*].PrivateIpAddress\' --output text >/tmp/inv'
            sh 'ansible-playbook -i /tmp/inv, roboshop.yml -e ansible_user=centos -e ansible-password=DevOps321 -e env=${env} -e role_name=${component}'
        }
    }

}

post { 
     always {
        cleanWs()
     }
}
}