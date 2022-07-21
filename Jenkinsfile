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
              
			    sh "mvn clean verify sonar:sonar \
                  -Dsonar.projectKey=dot-net-almutaywia \
                  -Dsonar.host.url=http://54.226.50.200 \
                  -Dsonar.login=sqp_5f67b5604d694e4862a1dd62c520ab1bdd04afd8"
			  
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