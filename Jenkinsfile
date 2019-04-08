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
      sh 'cp /opt/bitnami/apps/jenkins/jenkins_home/workspace/test_master/dist/hello-world.war /home/bitnami/hello-world/'
    }
    stage('run test') {  
     echo "hello"
    }
    stage('Docker_Build') {
      sh 'sudo docker build -t mvn-app --no-cache .'
    }
    stage('Deploy') {
      sh 'sudo docker run -d -p 8888:8888 mvn-app mvn-app'
    }
   }
  catch (err) {
    throw err
  }
}
