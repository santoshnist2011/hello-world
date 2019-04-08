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
    stage('Maven') {
      sh 'mvn clean '
      sh 'sudo cp /opt/bitnami/apps/jenkins/jenkins_home/workspace/test_master/dist/hello-world.war /home/bitnami/hello-world/
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
