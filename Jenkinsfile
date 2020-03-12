pipeline {
  agent any
  stages {
    stage('Git clone') {
      steps {
        sh '''cd /var/lib/jenkins/workspace/back_ami
git pull remote origin'''
      }
    }

    stage('Image Build') {
      steps {
        sh '''cd /var/lib
./packer build -var-file=/var/lib/jenkins/workspace/var.json /var/lib/jenkins/workspace/back_ami/AMI/packer/back_ami_build.json'''
      }
    }

    stage('Provisioning') {
      steps {
        sh '''cd /var/lib
./packer build -var-file=/var/lib/jenkins/workspace/var.json /var/lib/jenkins/workspace/back_ami/AMI/packer/back_ami_prov.json'''
      }
    }

  }
}