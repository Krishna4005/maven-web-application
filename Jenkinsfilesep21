node
{
def mavenHome = tool name: "maven3.8.2"

stage('checkoutcode')
{
git branch: 'development', credentialsId: '8e77ba0b-9a29-4922-a795-20347aaa5060', url: 'https://github.com/Krishna4005/maven-web-application.git'

}

stage('Build')
{
sh "${mavenHome}/bin/mvn clean package"     
}
stage('SonarQubeReport')
{
sh "${mavenHome}/bin/mvn clean sonar:sonar"

}

/*
stage('UploadArtifactIntoNexus')
{
sh "${mavenHome}/bin/mvn clean deploy"
}
stage('DeployAppIntoTomcatServer')
{
sshagent(['828947ce-c428-4fcd-89fd-4c5d01d857a2']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.232.143.255:/opt/apache-tomcat-9.0.52/webapps/"
}
}

*/
stage('SendEmailNotification')
{
emailext body: '''Build Over 

Regards 
Soujanyainfotech''', subject: 'Build Over ..', to: 'adimallakrishna53@gmail.com'
}

}
