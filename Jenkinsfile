pipeline{
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
    stage("build") {                      // 4  // Creates a stage named 'build'
            steps {                           // 5  // Defines the steps that will be executed in this stage
                echo "----------- build started ----------"  
                                              // Logs a message indicating the start of the build
                sh 'mvn clean deploy -Dmaven.test.skip=true'  
                                              // Runs Maven clean and deploy commands, skipping tests
                echo "----------- build completed ----------"  
                                              // Logs a message indicating the build completion
            }                                 // 5  // Ends the steps block for 'build' stage
        }                                     // 4  // Ends the 'build' stage

        stage("test") {                       // 6  // Creates a stage named 'test'
            steps {                           // 7  // Defines the steps that will be executed in this stage
                echo "----------- unit test started ----------"  
                                              // Logs a message indicating the start of unit tests
                sh 'mvn surefire-report:report'  
                                              // Runs the Maven Surefire report to execute unit tests
                echo "----------- unit test completed ----------"  
                                              // Logs a message indicating unit test completion
            }                                 // 7  // Ends the steps block for 'test' stage
        }        
            steps{
                withSonarQubeEnv('Devops-Sonaqube-server'){

                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}

