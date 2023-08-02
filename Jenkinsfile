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

//             stage ('upload artifect to S3 bucket'){
//                  steps{
//                         withAWS(credentials: 'S3_Backend', region: 'us-east-1') {
                                              echo 'Uploading to S3...'
                                              s3Upload(file:'/var/lib/jenkins/workspace/cafe/target/com.inn.cafe-0.0.1-SNAPSHOT.jar', bucket:'dominos1', path:'dominos1/com.inn.cafe-0.0.1-SNAPSHOT.jar')
                                              echo 'S3 upload Done.'
//                  }
//             }
        }
}