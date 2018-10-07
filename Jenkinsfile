node {
    stage('source'){
        git 'https://github.com/nagarameshreddy/myweb'
    }
    stage('Build'){
        bat 'mvn clean install'
    }
    stage('SonarQube'){
        bat 'mvn sonar:sonar'
    }
    stage('Nexus Upload'){
       nexusArtifactUploader artifacts: [[artifactId: 'myweb', classifier: 'releases', file: 'target/myweb.war', type: 'war']], credentialsId: '97811f5e-cca7-4767-8376-c47be4f5c349', groupId: 'in.javahome', nexusUrl: 'localhost:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'javahome1', version: '0.8.0-RELEASE'
    }
    stage('Jacoco'){
    jacoco()
    }
    stage('Mail'){
       mail bcc: '', body: 'Test Success', cc: '', from: '', replyTo: '', subject: 'test success', to: 'nagaramesh@outlook.com'    }
}

