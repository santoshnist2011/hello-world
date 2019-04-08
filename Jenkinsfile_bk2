pipeline {
  agent {
node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Environment') {
      sh 'git --version'
      echo "Branch: ${env.BRANCH_NAME}"
      sh 'docker -v'
      sh 'printenv'
    }
    stage('Build Maven App')
    {
      build 'mavne' 
    }
  }
  catch (err) {
    throw err
  }
}
}
}
