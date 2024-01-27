pipeline{
   agent any
    stages{
        stage("Starting Grid"){
            steps{
                step{
                bat "docker-compose -f grid.yaml up -d"
            }

            step{

                bat "docker-compose -f test-suites.yaml up"
            }

            }
           
        }
    }
    post{
        always{

            bat "docker-compose -f grid.yaml down"
            bat "docker-compose -f test-suites.yaml down"
            
        }
        
    }
}