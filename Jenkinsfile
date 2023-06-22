node
{
 
  stage("CheckOutCodeGit")
  {
   git credentialsId: '463010b4-b960-4164-bbcf-e0c4d003d2d6', url: 'https://github.com/janath-kumar/nodejs-app-mss.git'
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
 
stage("Build docker Image"){
   sh "docker build -t janathdocker/nodjsapplication:latest ."
}
 stage("docker login and Push"){
withCredentials([string(credentialsId: 'Docker_Hub_passwd', variable: 'Docker_Hub_passwd')])  
sh "docker login -u janathdocker -p ${Docker_Hub_passwd}"
sh "docker push janathdocker/nodjsapplication:latest ."
}
}
