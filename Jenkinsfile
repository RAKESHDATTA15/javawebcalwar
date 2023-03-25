node {
    stage('git clone') {
      git branch: 'main', url: 'https://github.com/THOTARAKESH/javawebcalwar.git'
    }
    stage('test') {
        // Run the maven build
        sh 'mvn  test'
    }
    stage('integration test') {
        // Run the maven build
        sh 'mvn verify -f /var/lib/jenkins/workspace/java/javawebcalwar/pom.xml -DskipUnitTest'
    }
    stage('build') {
        sh 'mvn clean -f /var/lib/jenkins/workspace/java/javawebcalwar/pom.xml install'
    }
    stage('nexus'){
        nexusArtifactUploader artifacts: 
        [
            [
                artifactId: 'WebAppCal', 
                classifier: '', 
                file: '/var/lib/jenkins/workspace/java/javawebcalwar/target/WebAppCal-0.0.2.war',
                type: 'war'
            ]
        ], 
        credentialsId: 'nexus', 
        groupId: 'com.web.cal', 
        nexusUrl: '3.12.152.152:49153', 
        nexusVersion: 'nexus3', 
        protocol: 'http', 
        repository: 'releases',
        version: '0.0.2'
    }  
}
