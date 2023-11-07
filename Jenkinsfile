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

    }

}