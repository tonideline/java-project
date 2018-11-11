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
sh ("aws s3 cp $WORKSPACE s3://tdeline-assignment-10/${JOB_NAME}/${BUILD_NUMBER}/ --recursive --exclude '*' --include '*.jar'")
  
}
stage('Report') { 
  withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'c934633f-4459-401f-80aa-d82aa16c9880', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
  sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
}
}
}
