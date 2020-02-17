def repo = "${REPO}_dvc"
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
	 stage('try catch check') {
            steps {
                script {
	                /*  Clone git Repo II */
	                sh "mkdir -p dvc_pipe; rm -rf dvc_pipe/${repo}"
	                /* Check if dvc repo exists */
	                try {
	                	sh "git ls-remote http://$REPO_CREDS_USR:$REPO_CREDS_PSW@${gitrepo}"
						}
	                catch (exc) {
	                	/* DVC repo does not exist: create from template*/
	                	sh "cd dvc_pipe; git clone http://$REPO_CREDS_USR:$REPO_CREDS_PSW@nttdata_os_codes.git"
	                	
	                	sh "cd dvc_pipe/nttdata_os_codes; git checkout -b ${branch} origin/${branch}"
	                	sh "cd dvc_pipe/nttdata_os_codes; git remote set-url origin http://$REPO_CREDS_USR:$REPO_CREDS_PSW@${gitrepo}"
	                	
	                	sh "cd dvc_pipe/nttdata_os_codes; git push http://$REPO_CREDS_USR:$REPO_CREDS_PSW@${gitrepo}"
	                	sh "rm -rf dvc_pipe/nttdata_os_codes"

                    }
                }      
               
            }  
        } 
	 stage('Chck python') {
            steps {
                sh "which python"
		sh "python --version"
		 //sh "which pip"   
		 // sh "which virtualenv"  
            }  
        }      
         
      }
    }










