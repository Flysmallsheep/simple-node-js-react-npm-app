pipeline {
   agent { docker 'openjdk:8-jdk-alpine' }
   stages {
      stage('Say Hello') {
         steps {
            sh 'java -version'
         }
      }
   }
}