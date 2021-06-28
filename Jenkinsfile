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
                    sh 'dotnet build Calculator.cs --configuration Release --no-restore'
                    
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
          echo "success - info zamiast maila, bo brak dostepu do tcp/25"
        }
        failure
        {
            echo "to bedzie wypisywane w razie faila"
        }
    }
}