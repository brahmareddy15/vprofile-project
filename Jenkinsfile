pipeline{

    agent any
         
        stage('Git Checkout'){
            steps{
            gitCheckout(
                branch: "rp-rem",
                url: "https://github.com/brahmareddy15/vprofile-project.git"
            )
            }
        }
         stage('Unit Test maven'){

            steps{
               script{
                   
                   mvnTest()
               }
            }
        }
         stage('Integration Test maven'){
            steps{
               script{
                   
                   mvnIntegrationTest()
               }
            }
        }
        stage('Maven Build : maven'){
            steps{
               script{
                   
                   mvnBuild()
               }
            }
        }
        stage('Docker Image Build'){
            steps{
               script{
                   
                   docker build -t  vprofile:v1  .
               }
            }
        }
        stage('Docker Image Push : DockerHub '){
            steps{
               script{
                   docker tag vprofile:v1 brahma00/vprofile:vi                 
               }
            }
        }   
        stage('Docker run application'){
            steps{
               script{
                   
                   docker run -d -p 8080:8080 vprofile:v1
               }
            }
        }      
    }
}
