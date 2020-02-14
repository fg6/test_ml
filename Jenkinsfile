def repo = "${REPO}"
def gitrepo = "github.com/Aimp91/${repo}.git"
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
                sh "git ls-remote https://$REPO_CREDS_USR:$REPO_CREDS_PSW@${gitrepo}"
                //sh "git ls-remote ${gitrepo}"
            }  
        }
         stage('try catch check') {
            steps {
                script {
	                /*  Clone git Repo II */
	                sh "mkdir -p dvc_pipe; rm -rf dvc_pipe/${repo}"
	                /* Check if dvc repo exists */
	                try {
	                	sh "git ls-remote http://$REPO_CREDS_USR:$REPO_CREDS_PSW@${gitrepo}"
	                catch (exc) {
	                	/* DVC repo does not exist: create from template*/
                        echo "non lo trovo"
                    }
                }      
               
            }  
        }  
         
      }
    }










