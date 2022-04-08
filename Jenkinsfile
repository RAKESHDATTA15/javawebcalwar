node {
    def mvnHome
    stage('clone') { // for display purposes
        git branch: 'main', url: 'https://github.com/THOTARAKESH/javawebcalwar.git'
    }
    stage('built-in') {
        sh 'mvn validate'
        sh 'mvn test'
        sh 'mvn clean package'
    }
    stage('deploy'){
        sh 'sudo cp -R /var/lib/jenkins/workspace/javapipe/target/WebAppCal-0.0.5.war  /home/centos/apache-tomcat-9.0.62/webapps/'
    }
}
