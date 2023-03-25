node {
    stage('test') {
        // Run the maven build
        sh 'mvn  test'
    }
    stage('integration test') {
        // Run the maven build
        sh 'mvn verify -DskipUnitTest'
    }
    stage('build') {
        sh 'mvn clean install'
    }
    stage('nexus'){
        def rakesh =  readMavenPom file: 'pom.xml'
        nexusArtifactUploader artifacts: 
        [
            [
                artifactId: 'WebAppCal', 
                classifier: '', 
                file: '/var/lib/jenkins/workspace/nexus/target/WebAppCal-0.0.3.war',
                type: 'war'
            ]
        ], 
        credentialsId: 'nexus', 
        groupId: 'com.web.cal', 
        nexusUrl: '3.12.152.152:49153', 
        nexusVersion: 'nexus3', 
        protocol: 'http', 
        repository: 'releases',
            version: "${rakesh}"
    }  
}
