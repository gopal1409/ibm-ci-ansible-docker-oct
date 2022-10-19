pipeline {
    agent any

   // tools {
        // Install the Maven version configured as "M3" and add it to the path.
     //   maven "M3"
    //}

    stages {
        stage('scm integration') {
            steps {
               
               git credentialsId: 'git-credentails', url: 'git@github.com:gopal1409/spring-chat-app-oct.git'
            }
        }
        stage('mvn build') {
            steps {
               
              sh 'mvn -Dmaven.test.failure.ignore=true clean package'
              //sh 'python app.py'
              // sh 'npm run'
              
            }
        }
        stage('unit test') {
            steps {
               //sh 'python xunit'
              sh 'mvn test'
              junit '**/target/surefire-reports/*.xml'
            }
        }
        stage('checkstyle') {
            steps {
               //sh 'python xunit'
              sh 'mvn checkstyle:checkstyle'
              recordIssues(tools: [checkStyle(pattern: '**/checkstyle-result.xml')])
              
              //junit '**/target/surefire-reports/*.xml'
            }
        }
     //    stage('sonar') {
          //  steps {
               
          //    sh 'mvn clean verify sonar:sonar \
  //-Dsonar.projectKey=chatapp \
 // -Dsonar.host.url=http://54.71.149.37:9000 \
 // -Dsonar.login=sqp_b51cdfe384f518c2b8f886cc4d4bf82987fca635'
              //sh 'python app.py'
              // sh 'npm run'
              
  //          }
 //       }
         stage('nexus') {
            steps {
               
              nexusArtifactUploader artifacts: [[artifactId: 'websocket-demo', classifier: '', file: 'target/websocket-demo-0.0.1-SNAPSHOT.jar', type: 'jar']], credentialsId: 'nexus-cred', groupId: 'websocket-demo', nexusUrl: '44.230.9.227:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'maven-snapshots', version: '0.0.1-SNAPSHOT'
              
            }
        }
    }
}

