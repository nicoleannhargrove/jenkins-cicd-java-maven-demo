
pipeline
{
    agent any
    tools
    {
        maven 'Maven'

    }
    stages
    {
        stage('Build')
        {
            steps
            {
                // Run the maven build
                echo 'going into the build stage'
                sh 'mvn clean install package'
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

