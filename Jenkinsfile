pipeline{
    agent any
    tools{
        maven 'maventool'
    }
    
    stages {
        stage("parallel stage"){
            parallel{
            
                 stage("code compile"){
                    steps{
                        sh "mvn compile"
                        echo "success"
                    }
                }
                 stage("testing of my code"){
                    steps{
                        sh "mvn test"
                    }   
                }
            }
        }
        stage("code quality check"){
            steps{
                sh "mvn pmd:pmd"
                recordIssues(tools: [pmdParser()])
            }
        }
        stage("package to be converted"){
            steps{
                sh "mvn package"
            }
        }
    }
}