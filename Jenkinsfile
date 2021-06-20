pipeline {
    agent { 
        docker { 
            image "python:3.8"
            args '--user 0:0'
        } 
        
    }
    environment {
       ROOT_FOLDER="${ROOT_FOLDER}"
       SF_ACCOUNT="${SF_ACCOUNT}"
       SF_USERNAME="${SF_USERNAME}"
       SF_ROLE="${SF_ROLE}"
       SF_WAREHOUSE="${SF_WAREHOUSE}"
       SF_DATABASE="${SF_DATABASE}"
       SNOWFLAKE_PASSWORD="${SF_PASSWORD}"
   }    
    stages {

        stage('Run schemachange') {
            steps {
                sh "pip install schemachange --upgrade"
                sh "schemachange -f ${ROOT_FOLDER} -a ${SF_ACCOUNT} -u ${SF_USERNAME} -r ${SF_ROLE} -w ${SF_WAREHOUSE} -d ${SF_DATABASE} -c ${SF_DATABASE}.SCHEMACHANGE.CHANGE_HISTORY --create-change-history-table"
            }
        }
    }
}