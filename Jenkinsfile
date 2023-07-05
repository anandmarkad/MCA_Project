pipeline{
        options{
                buildDiscarder(logRotator(numToKeepStr:'5',
                artifactNumToKeepStr:'5'))
        }
        agent any
        tools {
        maven 'maven_3.8.8'
        }

        stages{
            stage ('code compilation'){
                steps{
                echo 'code start compiling...'
                sh 'mvn clean compile'
                echo 'Code Compilation Done '
                }
            }

//             stage ('code Testing'){
//                   steps{
//                   echo 'code start testing...'
//                   sh 'mvn clean test'
//                   echo 'Code testing Done '
//                   }
//             }

            stage ('code packaging'){
                steps{
                echo 'code start packaging...'
                sh 'mvn clean package -DskipTests'
                echo 'Code packaging Done.'
                }
            }

//             stage ('code compilation'){
//                  steps{
//                        script{
//                        withCredentials([String(credentialsId:'S3_Backend')])
//                                       {
//                                       sh '
//                                       }
//                         }
//                  }
//             }
        }
}