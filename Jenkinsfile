pipeline {
    agent any
    environment {
        MainEnvConfig = 'someconfiguration2'
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
                    sh "${dotnet} build"
                }
            }
        }
        stage('Test') {
            steps {
                 dir("CalculatorTests"){
                    sh "${dotnet} test"
                }
            }
        }
        stage('Clean') {
            steps {
                 dir("Calculator"){
                    sh "${dotnet} clean"
                }
                  dir("CalculatorTests"){
                    sh "${dotnet} clean"
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
            mail to: 'kulik.piotr.it@gmail.com',
            subject: "build info",
            body: "build success"
        }
        failure
        {
            echo "to bedzie wypisywane w razue faila"
        }
    }
}