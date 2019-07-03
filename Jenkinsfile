node {
    stage('Code Checkout') { // for display purposes
     echo 'Checout Code and clone it inside jenkins workspace.'
     git 'https://github.com/thadiwada/sonar-maven.git'
   }
   stage('Build Test & Package') {
      echo 'Build the package'
      withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
       sh 'mvn clean compile'
     }
   }
   stage('sonarascanner') {
     withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
       withSonarQubeEnv('SONARID') {
         sh 'mvn verify sonar:sonar'   
       }
    }
  }
   stage('Artifacts') {
       echo 'package the project artifacts..'
       withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
       sh 'mvn package'
     }
   
   }
   stage('Deploy to Dev'){
       echo 'Deploy to Dev environment'
   }
   stage('Deploy to Test'){
       echo 'Deploy to Test environment'
   }
      stage('Test Automation'){
       echo 'Deploy to Dev environment'
   }
   
}
