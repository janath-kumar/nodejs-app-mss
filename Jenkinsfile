node
{
 
  stage("CheckOutCodeGit")
  {
   git credentialsId:'7b1ebfc6-dab3-4ffd-8112-9c12bc61c27d', url:'https://github.com/janath-kumar/nodejs-app-mss.git'
 }
 
 stage("Build")
 {
 nodejs(nodeJSInstallationName: 'nodejs15.2.1') {
        sh 'npm install'
    }
 }  
 	
 
 stage('RunNodeJsApp')
 {
 //sh "./scripts/run.sh"
 nodejs(nodeJSInstallationName: 'nodejs15.2.1') {
        sh 'npm start &'
    }
}    

stage("Build docker Image"){
   sh "docker build -t janathdocker/nodjsapplication:1."
}

stage("docker login and Push"){
withCredentials([string(credentialsId: 'Docker_Hub_passwd', variable: 'Docker_Hub_passwd')])
sh "docker login -u janathdocker -p ${Docker_Hub_passwd}"
sh "docker push janathdocker/nodjsapplication:1"
}

stage("Deploy Application in K8s Cluster"){
  sh "kubectl apply -f nodejsapplication.yaml"
}

}
