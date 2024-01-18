pipeline {
    agent { label 'slave2' }
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
            }
        }
        stage('Deploy') {
            steps {
                sh 'ssh root@172.31.28.191'
                sh 'cp /home/slave2/workspace/parcel_service_pipeline/target/simple-parcel-service-app-1.0-SNAPSHOT.jar root@172.31.28.191:/opt/apache-tomcat-8.5.98/webapps/'
        }
        }
    } 
}

    
