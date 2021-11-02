pipeline {
   agent any
   parameters {
        booleanParam(name: 'RC', defaultValue: false, description: 'Is this a Release Candidate')
   }
   environment {
       VERSION= "0.1.0"
       VERSION_RC = "rc.2"
   }

   stages {
      stage('Audit tools') {
         agent any
         steps {
            bat '''
                git version
            '''
         }
      }
      stage('build') {
            environment {
                VERSION_SUFFIX = getVersionSuffix()
            }
           steps {
              echo "Building version: ${VERSION} with suffix: ${VERSION_SUFFIX}..."
           }
      }

      stage('Unit Test'){
         steps{
            echo "Testing"
         }
      }
   }
   post {
        always{
            echo "Prints wehter eply happend or not, success or failure"
        }
   }
}

String getVersionSuffix(){
    if(params.RC){
        return env.VERSION_RC
        }
    else {
        return env.VERSION_RC + '+ci.' + env.BUILD_NUMBER
    }
}