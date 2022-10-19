pipeline {
    agent any

   // tools {
        // Install the Maven version configured as "M3" and add it to the path.
     //   maven "M3"
    //}

    stages {
        stage('scm stage') {
            steps {
                // Get some code from a GitHub repository
             git credentialsId: 'git-credentails', url: 'git@github.com:gopal1409/-ansible-cd-pipeline-ibm-devops-oct221.git'   
            }
        }
         stage('Build') {
            steps {
                // Get some code from a GitHub repository
             sh 'mvn clean package'  
            }
        }
        stage('ansible') {
            steps {
                // Get some code from a GitHub repository
                ansiblePlaybook credentialsId: 'git-credentails', disableHostKeyChecking: true, inventory: 'ansible/dev.inv', playbook: 'ansible/tomcat.yml'
            }
        }
    
    }
}

