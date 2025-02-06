node{
    
    echo "the Job name is : ${env.JOB_NAME}"
    echo "the node name is: ${env.NODE_NAME}"
    echo "the build number is: ${env.BUILD_NUMBER}"
    
properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '5', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
    
def mavenHome = tool name: 'Maven_3.9.9'
stage('CheckOutCode'){
git credentialsId: 'github_cred', url: 'https://github.com/Akshithakjr/maven-web-application.git'
}

stage('build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('Sonarqubereport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}
stage('Sonarqubereport'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployApptoTomcatserver'){
sshagent(['8d11d3f8-002a-4f75-bd26-31344a882b3d']) {
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.40.69:/opt/apache/webapps/"
}
}
*/
}
