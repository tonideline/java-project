properties([pipelineTriggers([githubPush()])])

node('linux') { 
  stage('Unit Tests') {
   git 'https://github.com/tonideline/java-project.git'
   sh 'ant -f test.xml -v'
}
stage('Build') { 
  sh 'ant'
  sh 'ant -f build.xml -v '
}
stage('Results') {
 junit 'reports/result.xml' }

}
