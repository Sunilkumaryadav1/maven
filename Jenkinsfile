node {
   stage('git_checkout') {
       git 'https://github.com/Sunilkumaryadav1/maven.git'
   }
   stage('build') {
          sh 'mvn package'
   }
  stage('deploy') {
    deploy adapters: [tomcat9(credentialsId: 'tomcat-credentials', path: '', url: 'http://172.31.7.92:8080')], contextPath: 'qaapp', war: '**\\*.war'
   } 
   stage('testing')
   { git 'https://github.com/Sunilkumaryadav1/Testing.git'
     sh 'java -jar /var/lib/jenkins/workspace/pipe1/testing.jar'
   }
   stage('delivery') {
    deploy adapters: [tomcat9(credentialsId: 'tomcat-credentials', path: '', url: 'http://172.31.3.191:8080')], contextPath: 'qaapp', war: '**\\*.war'
   } 
}
