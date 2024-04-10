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
                export MAVEN_HOME=/opt/maven
                export PATH=$PATH:$MAVEN_HOME/bin
                mvn --version
                mvn clean package
                '''
            }
        }
    }

}