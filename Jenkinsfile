pipeline{
    agent any
    tools{
        maven 'Maven'
    }
    parameters{
        string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }   
    environment{
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('creds')
    }
    stages{
        stage("build"){
            steps{
                echo 'building the app'
                echo "version ${NEW_VERSION}"
            }
        }
        stage("test"){
            steps{
                echo 'testing the app' 
            }
        }
        stage("deploy"){
            steps{
                echo 'deploying the app'
               
                 echo 'deploying the app'
                 withCredentials([
                       usernamePassword(credentials: 'sserver-credentials', usernameVariable: 'USER', passwordVariable: 'PASSWORD')
                         ]) {
                echo "Username: $USER"
                echo "Password: $PASSWORD"
            }
        }
    }
}

post{
    always{
        
    }
    success{
        echo "done!"
    }
    failure{
        echo "failed!"
    }
}