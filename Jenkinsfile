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
              
			    sh 'dotnet tool install --global dotnet-sonarscanner"
                    dotnet sonarscanner begin /k:"dot-net-almutaywia" /d:sonar.host.url="http://54.226.50.200"  /d:sonar.login="sqp_5f67b5604d694e4862a1dd62c520ab1bdd04afd8"
                    dotnet build
                    dotnet sonarscanner end /d:sonar.login="sqp_5f67b5604d694e4862a1dd62c520ab1bdd04afd8"'
			    
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