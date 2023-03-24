node {
    stage('docker-log'){
        withCredentials([string(credentialsId: 'docker1', variable: 'dockerlog')]) {
            sh 'docker login -u rakeshdatta12 -p ${dockerlog}'
        }
    }
    stage('write-Dockerfile') { 
        writeFile file:'Dockerfile',text:'FROM rakeshdatta12/java'
    }
    stage('Build') {
        sh 'docker build --build-arg url=https://github.com/THOTARAKESH/javawebcalwar.git -t rakeshdatta12/java-auto   .'
        }
    stage('Results') {
        sh 'docker container run -dt --name ${tag} -p ${value}:8080 rakeshdatta12/java-auto '
    }
    stage('see'){
        sh 'docker container ps && docker image ls '
    }
}
