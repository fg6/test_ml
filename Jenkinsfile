def repo = "${REPO}_DVC"
def gitrepo = "github.com/Aimp91/${REPO}.git"
pipeline {
    agent any
     environment { 
        REPO_CREDS = credentials("gitcreds1")
     }
      stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }  
        }
        stage('Repo check') {
            steps {
                echo "${repo}"
            }  
        }
         stage('Check cred') {
            steps {
                //sh "git ls-remote https://$REPO_CREDS_USR:$REPO_CREDS_PSW@${gitrepo}"
                sh "git ls-remote http://github.com/Aimp91/test_ml.git"
            }  
        }  
      }
    }










