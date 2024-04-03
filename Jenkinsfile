pipeline {

    agent any
    tools {
        maven 'Maven'
    }

    stages {
        // stage('Initialize') {
        //     steps {
        //         sh '''
        //             echo "PATH = ${PATH}"
        //             echo "M2_HOME = ${M2_HOME}"
        //         '''
        //     }
        // }
        stage('build') {
            steps {
                sh '''
                mvn --version
                mvn clean package
                '''
            }
        }
        stage('deploy') {
            steps {
                sshagent(['tomcat']) {
                    sh "ssh -o StrictHostKeyChecking=no ubuntu@13.233.22.107 'ls'"
                    sh "ssh -o StrictHostKeyChecking=no ubuntu@13.233.22.107 'sudo su'"
                    sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@13.233.22.107:/home/ubuntu/prod/apache-tomcat-9.0.87/webapps/'
                }
            }
        }
    }

}