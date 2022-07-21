pipeline {

    agent any

    stages {

        stage('Build'){
            steps {
                

                sh "dotnet restore"
            }
        }

        stage('Test'){
            steps {
                
                sh "dotnet test"
            }

        }

        stage('sonar scan'){
            steps {
              
			  sh 'mvn clean verify sonar:sonar \
  -Dsonar.projectKey=almutaywia \
  -Dsonar.host.url=http://54.226.50.200 \
  -Dsonar.login=sqp_a90bc30ff7480dba3b87cbbfa433c4a079959fa5'
			  
            }
        }

        stage('Package'){
            steps {
                
                sh "dotnet publish"
            }
            post {
                success {
                    archiveArtifacts artifacts: '**/*.dll', followSymlinks: false
                }
            }
        }

    }

}