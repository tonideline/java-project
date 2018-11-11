properties([pipelineTriggers([githubPush()])])

node('linux') { 
  stage('Unit Tests') {
   git 'https://github.com/tonideline/java-project.git'
   sh 'ant -f test.xml -v'
   sh 'ant -buildfile reports/result.xml' 
}
stage('Build') { 
  sh 'ant -f build.xml -v '
}
stage('Results') {
 junit 'reports/result.xml' }

}
