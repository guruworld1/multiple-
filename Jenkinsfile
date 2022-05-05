node('build-in') 
{
    stage('Continuous Download')
                   {
                     git branch: 'feature', credentialsId: 'github', url: 'https://github.com/Zubby19/multiple-.git'
                   }
    stage('Continuous build')
                   {
                    sh 'mvn package'
                   }
    stage('Continuous deployment')
                   {
                    deploy adapters: [tomcat8(credentialsId: 'dev', path: '', url: 'http://172.31.30.93:8080')], contextPath: 'qaenv', war: '**/*.war'
                   }
    stage('Continuous testing')
                   {
                    sh 'echo "testing has passed"'
                   }
     stage('Continuous delivery')
                   {
                    input message: 'Waiting for approval from executor', submitter: 'zubby19'
                    deploy adapters: [tomcat8(credentialsId: 'prod', path: '', url: 'http://172.31.21.148:8080')], contextPath: 'prod', war: '**/*.war'
                   }
}
