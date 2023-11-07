pipeline {
    agent any

    stages {
        stage ('GIT') {
            steps {
                echo "Getting project from Git"
                git branch: "master", 
                    credentialsId: 'github_id',
                    url: "https://github.com/maeva-bot/Devops-project.git";
            }
        }

    stage("Clean") {
            steps {
                script {
                    echo "clean with Maven..."
                    sh 'mvn clean compile'
                }
            }
     }

    stage("Maven Build") {
            steps {
                script {
                    echo "Building with Maven..."
                    sh "mvn package -DskipTests=true"
                }
            }
        }



    stage("Deploy to nexus") {
            steps {
                echo "Deploy to nexus..."
                sh "mvn deploy -DskipTests=true"
      
      
      
            }
    }


    stage('SonarQube'){
            steps{
                withSonarQubeEnv('SonarQube'){
                    echo "Running SonarQube analysis..."
                    sh "mvn sonar:sonar -Dsonar.projectKey=maven-jenkins-pipeline -Dsonar.host.url=http://192.168.33.10:9000 -Dsonar.login=907af9eea8f2240873cab7b42ee1dc1395d6ea5c"
                    
            }
                }
                
        }


















    }



}