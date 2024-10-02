pipleline{
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }

    stages{
        stage("build"){
            steps{
                sh 'mvn clean deploy'
                }
        }
        stage('SonarQube analysis'){
            environment {
                scannerHome = tool 'Code-scanner-sonar'

            }
            steps{
                withSonarQubeEnv('Devops-Sonaqube-server'){

                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}
