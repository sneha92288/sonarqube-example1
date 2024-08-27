// pipeline{
//     agent {label 'jfrog'}
//     stages{
//        stage('Git Checkout Stage'){
//             steps{
//                 git branch: 'main', url: 'https://github.com/artisantek/sonarqube-example.git'
//             }
//          }        
//        stage('Build Stage'){
//             steps{
//                 sh 'mvn clean install'
//             }
//          }
//         stage('SonarQube Analysis Stage') {
//             steps{
//                 withSonarQubeEnv('sonarqube') { 
//                     sh "mvn clean verify sonar:sonar -Dsonar.projectKey=sonar-test"
//                 }
//             }
//         }
//     }
// }

pipeline {

   agent {

      node {

          label 'maven'

    }

}

 

environment {

  PATH= "/opt/apache-maven-3.9.2/bin/:$PATH"

}

  stages {

    stage("build"){

       steps{

          sh "mvn clean deploy"

       }

    }

   stage("SonarQube analysis"){

   environement {

      scannerHome = tool 'sonarqubr=server'

   }

   steps{

   def scannerHome = tool 'sonarqube-serverr";

   withSonarQubeEnv("my SonarQube server")

     sh "${scannerHome}/bin/sonar-scanner"

    }

    }

   }

  }


