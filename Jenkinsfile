pipeline{

    agent any

    stages{
        stage("Sonar quality check"){
            agent{
                docker{
                    image "openjdk:11"
                }
            }
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonar-token') {
                        sh 'java --version'
                        sh "chmod +x gradlew"
                        sh "/var/lib/jenkins/workspace/java-gradle-application/gradlew --warning-mode fail --stacktrace sonarqube"
                    }
                }
            }
        }
    }
}