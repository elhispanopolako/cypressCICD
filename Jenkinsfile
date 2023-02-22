pipeline{
    agent any
    parameters{
        string(name: 'SPEC',defaultValue: "cypress/e2e/**/**",description:"Enter the script path that you wanted execute")
        choice(name:'BROWSER',choices:[chrome,electron],description:"Choice the browser where you want to execute ypur script")
    }
    options{
        ansiColor('xterm')
    }
    stages{
        stage('Building'){
            steps{
            echo "Building the app"

            }
        }
        stage('Testing'){
            steps{
                bat "npm i"
                bat "npx cypress run --browser ${BROWSER} --spec ${SPEC}"
            }
        }
        stage('Deploying'){
            steps{
            echo "Deploying the app"

            }
        }
    }
    post{
        always{
            publishHTML (target : [allowMissing: false, alwaysLinkToLastBuild: true,keepAll: true,reportDir: 'cypress/reports/html',reportFiles: 'index.html',reportName: 'My Reports',reportTitles: 'The Report'])
        }
    }
}