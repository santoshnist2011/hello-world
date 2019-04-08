node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Environment') {
      echo "$USER"
      sh 'git --version'
      echo "Branch: ${env.BRANCH_NAME}"
      sh 'printenv'
    }
    stage('Maven') {
      sh 'mvn clean '
      sh 'cp /opt/bitnami/apps/jenkins/jenkins_home/workspace/HelloWorld/dist/hello-world.war /home/bitnami/hello-world/'
    }
    stage('run test') {  
     sh 'mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent test'
     sh ' mvn package sonar:sonar -Dsonar.host.url=http://35.154.234.38:9000'
    }
    stage('Docker_Build') {
      sh ' sudo docker build -t mvn-app --no-cache .'
    }
    stage('Deploy') {
      sh ' sudo docker run -it --rm -p 8080:8080 --name mvn-app mvn-app'
    }
   }
  catch (err) {
    throw err
  }
}
