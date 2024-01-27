pipeline{
    agent any

stages{

stage("Running Grid"){
    steps{bat "docker-compose -f grid.yaml up -d"}
}
stage("Running Tests"){
    steps{bat "docker-compose -f test-suites.yaml up"}
}



}

post{

    always{bat "docker-compose -f grid.yaml down"
            bat "docker-compose -f test-suites.yaml down"
            archiveArtifacts artifacts: 'output/Rajat-portal/emailable-report.html', followSymlinks: false
            }
}



}