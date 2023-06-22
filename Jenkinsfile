node
{
 
  stage("CheckOutCodeGit")
  {
   git credentialsId:'7b1ebfc6-dab3-4ffd-8112-9c12bc61c27d', url:'https://github.com/janath-kumar/nodejs-app-mss.git'
 }

 stage("Build")
 {
 nodejs(nodeJSInstallationName: 'nodejs20.3.1') {
        sh 'npm install'
    }
 }  

stage('RunNodeJsApp')
 {
 //sh "./scripts/run.sh"
 nodejs(nodeJSInstallationName: 'nodejs20.3.1') {
        sh 'npm start &'
    }
}    
}
