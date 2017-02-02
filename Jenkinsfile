node('master') {
    def workSpaceHome = pwd()
    stage('Clean') {
        deleteDir()
    }
    stage('Checkout') {
        checkout scm
    }
    stage('Grunt Process') {
        sh """
            cd Grunt
            npm install
            grunt
        """
    }
    stage('Run') {
       withMaven(jdk: 'JDK', maven: 'maven3', mavenLocalRepo: '', mavenOpts: '', mavenSettingsFilePath: '') {
           sh "mvn test"
       }
    }
}