
pipeline
{
    agent any
    stages
    {
        stage('Build')
        {
            steps
            {
                // Run the maven build
                echo 'going into the build stage'
                export Maven_HOME=/opt/apache-maven-3.8.6
                export PATH+$PATH:$MAVEN_HOME/bin
                mvn --version
                sh 'mvn clean install'
                echo 'Finished with maven finally'
            }

        }

        stage('Deploy')
        {
            steps
            {
                echo 'going into the Deply stage'
                //deploy war on tomcat server
                deploy adapters: [tomcat9(url: "${tomcatServerUrl}",
                credentialsId: 'tomcat-credentials')],
                war: 'target/*.war',
                contextPath: 'pipeline-app'
                echo 'war file has been deployed'

            }
        }
    }
  }

