pipeline {
  agent any 
    stages {
      stage ('Lint HTML') {
        steps {
          tidy -q -e *.html
        }
      }
      stage('Upload to AWS') {
        steps {
          withAWS(region:'us-east-1',credentials:'aws-static') {
              s3Delete(bucket: 'shewitinv-jenkins', path:'')
              s3Upload(file: 'index.html', bucket: 'shewitinv-jenkins', path: 'index.html');
          }
        }
      }
   }
}
