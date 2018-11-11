properties([pipelineTriggers([githubPush()])])

node('linux') { 
  stage('Unit Tests') {
   git 'https://github.com/tonideline/java-project.git'
   sh 'ant -f test.xml -v'
   sh 'ant -buildfile results.xml' 
}
stage('Build') { sh 'ant -f '
}
stage('Results') {
 junit 'reports/results.xml' }

}
