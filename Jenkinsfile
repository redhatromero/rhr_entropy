pipeline {

environment {
  BUILD_SCRIPTS_GIT="https://github.com/redhatromero/rhr_entropy.git"
  BUILD_SCRIPTS='rhr_entropy'
  BUILD_HOME='/var/lib/jenkins/workspace'
}

agent any

stages {
  stage('Checkout: Code') {
    steps {
      sh "mkdir -p $WORKSPACE/repo;\
      git config --global user.email 'redhatromero@gmail.com';\
      git config --global user.name 'redhatromero';\
      git config --global push.default simple;\
      git clone $BUILD_SCRIPTS_GIT repo/$BUILD_SCRIPTS"
      sh "chmod -R +x $WORKSPACE/repo/$BUILD_SCRIPTS"
      }
  }

  stage('Yum: Updates') {
    steps {
      #sh "sudo chmod +x $WORKSPACE/repo/$BUILD_SCRIPTS/scripts/update.sh"
      #sh "sudo $WORKSPACE/repo/$BUILD_SCRIPTS/scripts/update.sh"
      sh "sudo yum update"
      }
  }
}

post {
  always {
    cleanWs()
    }
  }
}
}
