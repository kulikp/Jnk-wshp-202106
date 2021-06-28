pipeline {
    agent any
    environment {
        MainEnvConfig = 'someconfiguration'
        dotnet = '"C:\\Program Files\\dotnet\\dotnet.exe"'
    }
    stages {
         stage('Env') {
            when {
                branch 'main'
            }
            steps {
                echo "we need to do ${MainEnvConfig} in order to make it work"
            }
        } 
        stage('Scripts') {
             steps {
               script{
                   def a = 5
                   println a
                   if(a>3)
                   {
                       println "a jest wieksze od 3"
                   }
                   else
                   {
                       println "a jest mniejsze badz rowne 3"
                   }
               }
            }
        }
        stage('Build') {
            steps {
                dir("Calculator"){
                    
                }
            }
        }
        stage('Test') {
            steps {
                 dir("CalculatorTests"){
                    
                }
            }
        }
        stage('Clean') {
            steps {
                 dir("Calculator"){
                    
                }
                  dir("CalculatorTests"){
                    
                }
            }
        }
    }
    post 
    {
        always
        {
            echo "to zawsze bedzie wypisywane"
        }
        success
        {
            mail to: 'piotr.kulik@posti.com',
            subject: "build info",
            body: "build success"
        }
        failure
        {
            echo "to bedzie wypisywane w razie faila"
        }
    }
}