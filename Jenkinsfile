node {
    stage('Code Checkout') { // for display purposes
     echo 'Checout Code and clone it inside jenkins workspace.'
     git 'https://github.com/thadiwada/sonar-maven.git'
   }
   stage('Build Test & Package') {
      echo 'Build the package'
      withMaven(maven:'Maven_3_3_9', mavenLocalRepo: '.repository',mavenSettingsConfig:'my-config') {
      sh 'mvn clean install'
     }
   }
   stage('sonarascanner') {
     withMaven(jdk: 'JDK-1.8', maven: 'Maven3.6.1') {
       withSonarQubeEnv('SONARID') {
         sh 'mvn verify sonar:sonar'   
       }
    }
  }
   stage('Artifacts') {
       echo 'package the project artifacts..'
       withMaven(jdk: 'JDK-1.8', maven: 'MAVEN') {
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
