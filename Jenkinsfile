node {
    def mavenHome = tool name: "maven3.8.6"
    
    
    stage('checkourcode'){
       git branch: 'development', credentialsId: '679764c7-83e3-4f45-8daf-41d95c63e4c0', url: 'https://github.com/Asra1997/maven-web-application.git' 
    }
    
    
    stage('build'){
    sh "${mavenHome}/bin/mvn clean package"
}


stage('sonarqubereport'){
    sh "${mavenHome}/bin/mvn sonar:sonar"
}


stage('uploadtoartifactrepository'){
    sh "${mavenHome}/bin/mvn deploy"
}

sshagent(['77d836cd-9f4b-48bb-90aa-7977f717dca6']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@35.182.154.128:/opt/apache-tomcat-9.0.68/webapps"
    
}

}
