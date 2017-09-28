pipeline {
    agent { label 'centos-7' }
    tools {
        maven 'Maven_3.5.0'
        jdk 'JDK_8u111'
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        } 
        stage('Build') {
            steps {
                sh "mvn' -Dmaven.test.failure.ignore clean package"
            }
            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                }
            }
        }
    }
}