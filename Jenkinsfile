pipeline {
     agent any
    stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World"'
                 sh ''' 
                    echo "Multiline shell steps works too"
                    '''
             }
         }
         stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }
         stage('Upload to AWS') {
            steps {
                withAWS(region:'eu-west-1',credentials:'aws-cred') {
                sh 'echo "Uploading content with AWS creds"'
                    s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'udacity-cloud4-cicd-sg860119-eu-west-1')
                }
            }
        }
     }
}
