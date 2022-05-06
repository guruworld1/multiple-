node('slave.jar') 
{
    stage('continue download ') 
    {
     git branch: 'feature ', credentialsId: 'zubby', url: 'https://github.com/ttnwt/webapp.git'   
}
   stage('continue build ') 
    {
      sh 'mvn package '
}
 stage('continue deploy ') 
    {
     deploy adapters: [tomcat8(credentialsId: 'dev', path: '', url: 'http://172.31.30.93:8080')], contextPath: 'qaenv', war: '**/*.war' 
}
 stage('continue testing ') 
    {
      sh 'echo " emma said go ask nonso is successful"'
}
stage('continue deliver to nonso and emma ') 
    {
   deploy adapters: [tomcat8(credentialsId: 'git', path: '', url: 'http://172.31.21.148:8080')], contextPath: 'prod', war: '**/*.war'   
}
}
