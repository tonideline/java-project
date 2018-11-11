properties([pipelineTriggers([githubPush()])])

node('linux') { 
  stage('Unit Tests') {
   git 'https://github.com/tonidelinejava-project.git'
   sh 'ant -f test.xml -v'
   sh 'ant -buildfile results.xml' 
}

stage('Results') {
 junit 'reports/results.xml' }

}
