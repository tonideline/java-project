properties([pipelineTriggers([githubPush()])])

node('linux') { 
  stage('Unit Tests') {
   git 'https://github.com/tonideline/java-project.git'
   sh 'ant -f test.xml -v'
}
stage('Results') {
 junit 'reports/result.xml' }

 stage('Build') { 
  sh 'ant'
  sh 'ant -f build.xml -v '
}

stage('Deploy') { 
sh ("aws s3 cp $WORKSPACE/target/ s3://tdeline-assignment-10/${JOB_NAME}/${BUILD_NUMBER}")
  
}

}
