pipeline {
   agent any
   
   environment {
       RELEASE='20.04'
   }

   stages {
      stage('build') {
         agent any

         environment {
               LOG_LEVEL='INFO'
         }

         steps {
            echo "Building release ${RELEASE} with log level ${LOG_LEVEL}..."
         }
      }
      stage('test') {
               steps {
                  echo "Testing. I can see release ${RELEASE}..."
               }
      }

      stage('Deploy'){
        input {
            message 'Deploy?'
            ok 'Do it!'
            parameters {
                string(name: 'TARGET_ENVIRONMENT', defaultValue: 'PROD', description: 'Target Deployment environment')
            }
        }
         steps{
            echo "Deploying release ${RELEASE} to environment ${TARGET_ENVIRONMENT}"
         }
      }
   }
   post {
        always{
            echo "Prints wehter eply happend or not, success or failure"
        }
   }
}