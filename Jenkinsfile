pipeline{
    agent any
    stages{
        stage('Build Backend'){
            steps{
               bat 'mvn clean package -DskipTests=true'
            }    
        }
        stage('Sonar Analysis'){
            steps{
               bat 'mvn test'
            }    
        }
        stage('Sonar Analysis'){
            environment{
                scannerHome = tool 'SONAR_SCANNER'
            }
            steps{
                withSonarQubeEnv('SONAR_SCANNER'){
                  bat "${SONAR_SCANNER}/bin/sonar-scanner -e -Dsonar.projectKey=DeployBack -Dsonar.host.url=http://localhost:9000 -Dsonar.login=32fb764884456aeb7cf5a695c976262020109c4f -Dsonar.java.binaries=target -Dsonar.coverage.exclusions=**/.mvn/**,**/src/test/**,**/model/**,**Application.java"
                }    
            }    
        }
    }
}

 

