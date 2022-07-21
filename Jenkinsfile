pipeline {
    agent any
    environment {
        SONAR_IP = "54.226.50.200"
        SONAR_TOKEN ="sqp_14416226962f90245e5910c676578eb661c04d62"     
    }

    stages {
        stage('Restore') {
            steps {
                sh "dotnet restore"

            }
        }
         stage('Build') {
            steps {
                sh "dotnet build"
            }
        }
         stage('Test') {
            steps {
                sh "dotnet test"
            }
        }
        // stage('Quality Scan'){
        //     steps {
        //         sh '''
        //             /usr/bin/dotnet /home/ubuntu/.dotnet/tools/dotnet-sonarscanner begin /k:"dotnet-project" /d:sonar.host.url=$SONAR_IP /d:sonar.login=$SONAR_TOKEN
        //             /usr/bin/dotnet build
        //             /usr/bin/dotnet /home/ubuntu/.dotnet/tools/dotnet-sonarscanner end /d:sonar.login=$SONAR_TOKEN
        //         '''
        //     }
        // }
         stage('Publish') {
            steps {
                sh "dotnet publish"
            }
            post{
                success{
                    archiveArtifacts artifacts: '**/bin/Debug/net6.0/**.dll', followSymlinks: false

                    
                }
            }
        }
        

    }
}


 