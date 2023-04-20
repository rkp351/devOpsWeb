pipeline {
    agent any

    stages {
        stage('Maven-Build') {
            steps {
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Success"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage('Deploy to Tomcat Server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'Tomcat_Creds', path: '', url: 'http://54.86.171.65:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
