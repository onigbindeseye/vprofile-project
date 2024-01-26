pipeline{
    agent any
    tools {
        maven 'MAVEN3'
        jdk 'OracleJDK11'
    }
    stages {
        stage('Fetch Code'){
            steps {
                git branch: 'main', url: 'https://github.com/onigbindeseye/vprofile-project.git'
            }
        }
        stage('Build'){
            steps {
                sh 'mvn install -DskipTests'
            }
            post {
                success{
                    echo 'Artifact Archive'
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage ('UNIT TESTS') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
