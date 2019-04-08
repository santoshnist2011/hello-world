node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Environment') {
      sh 'git --version'
      echo "Branch: ${env.BRANCH_NAME}"
      sh 'printenv'
    }
    stage('Maven ) {
      sh 'mvn clen '
    }
    stage('run test') {  
     echo "hello"
    }
    stage('Docker_Build') {
      echo "ddd"
    }
   }
  catch (err) {
    throw err
  }
}
