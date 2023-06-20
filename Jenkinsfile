node
{
 
  stage("CheckOutCodeGit")
  {
   git credentialsId:'7b1ebfc6-dab3-4ffd-8112-9c12bc61c27d', url:'https://github.com/janath-kumar/nodejs-app-mss.git'
 }

 stage("Build")
 {
 nodejs(nodeJSInstallationName: 'nodejs16.19.1') {
        sh 'npm install'
    }
 }  
 
}
