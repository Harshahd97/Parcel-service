pipeline {
    agent { label 'slave2' }
    environment {
    MAVEN_HOME = tool 'Maven'
}
    stages {
        stage('Checkout') {
            steps {
                sh 'rm -rf Parcel-service'
                sh 'git clone https://github.com/Harshahd97/Parcel-service.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn --version'
                sh 'mvn clean install'
                sh 'mvn spring-boot:run'
                sh '${MAVEN_HOME}/bin/mvn clean package'
            }
        }
         stage('Run Locally') {
        steps {
                sh "java -jar target/simple-parcel-service-app-1.0-SNAPSHOT.jar &"
                sleep 30
            }
         }
        stage('Deploy') {
            steps {
                sh 'ssh root@172.31.28.191'
                sh 'scp /home/slave2/workspace/parcel_service_pipeline/target/simple-parcel-service-app-1.0-SNAPSHOT.jar root@172.31.28.191:/opt/apache-tomcat-8.5.98/webapps'
        }
        }
    } 
}
