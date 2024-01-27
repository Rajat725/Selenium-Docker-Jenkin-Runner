pipeline{
    agent any

    parameters {
  choice choices: ['chrome'], description: 'Please select the browser', name: 'BROWSER'
}


stages{

stage("Running Grid"){
    steps{bat "docker-compose -f grid.yaml up --scale ${params.BROWSER}=2 -d"}
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