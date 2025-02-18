pipeline{
    agent any
    environment {
        PATH = "$PATH:/opt/apache-maven-3.9.9/bin"
    }
    stages{
       stage('Checkout'){
            steps{
                git 'https://github.com/padinarayanareddy/Sonar-Project.git'
            }
         }        
       stage('Package'){
            steps{
                sh 'mvn clean package'
            }
         }
        stage('SonarQube analysis') {
//    def scannerHome = tool 'SonarScanner 4.0';
        steps{
        withSonarQubeEnv('SonarQube') { 
        // If you have configured more than one global server connection, you can specify its name
//      sh "${scannerHome}/bin/sonar-scanner"
        sh "mvn clean verify sonar:sonar -Dsonar.projectKey=Sonar-project -Dsonar.host.url=http://13.233.236.189:9000/ -Dsonar.login=sqp_6be8a6967e91f13ce3c6a27dc499f63e9c7b76f8"
                }
            }
        }
    }
}
