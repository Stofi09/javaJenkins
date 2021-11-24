pipeline {
    agent any
    tools {
        maven "MavenInstall"
        jdk "JDK"
    }
    stages {
        stage('Initialize'){
            steps{
                echo "PATH = /usr/lib/jvm/java-11-openjdk-amd64"
                echo "M2_HOME = /opt/maven"
            }
        }
        stage('Build') {
            steps {
                dir("/var/lib/jenkins/workspace/demopipelinetask/my-app") {
                sh 'mvn -B -DskipTests clean package'
                }
            }
        }
     }
    post {
       always {
          junit(
        allowEmptyResults: true,
        testResults: '*/test-reports/.xml'
      )
      }
   }
}
