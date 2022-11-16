
pipeline {

    stage('Build') {
      steps {
        // Run the maven build
        sh '"mvn" -Dmaven.test.failure.ignore clean install build'
      }

    }
    stage('Deploy') {
      steps {
        //deploy war on tomcat server
        deploy adapters: [tomcat9(url: "${tomcatServerUrl}",
            credentialsId: 'tomcat-credentials')],
          war: 'target/*.war',
          contextPath: 'pipeline-app'

      }
    }
  }
}
