pipeline {
    agent any
    
    environment {
        REPO_URL = "https://github.com/Sheikhatiff/resume-"
        BRANCH = "main"
        TARGET_DIR = "/var/www/resume-ai"
        GIT_CREDS = "github-pat"
    }
    
    stages {
        stage('Update Repository') {
            steps {
                script {
                    if (fileExists("${env.TARGET_DIR}/.git")) {
                        echo "Repository exists. Pulling latest changes..."
                        
                        dir(env.TARGET_DIR) {
                            sh "git pull origin ${env.BRANCH}"
                        }
                    } else {
                        echo "Repository not found. Cloning..."

                        dir(env.TARGET_DIR) {
                            git(
                                branch: env.BRANCH,
                                credentialsId: env.GIT_CREDS,
                                url: env.REPO_URL
                            )
                        }
                    }
                }
            }
        }
    }
}
