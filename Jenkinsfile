pipeline {
     agent any
     tools {
               go 'default-go'
          }    
     stages {
          stage("SCM Checkout") {
               steps {
                    git 'https://github.com/vishureddy/Jenkins_CI.git'
               }
          }
          stage("Pre-Test") {
               steps {
                    sh "go get -u golang.org/x/lint/golint"
                    sh "go get -u github.com/logrusorgru/aurora"
               }
          }
          stage("Testing") {
               steps {
                     sh "go fmt"
                     sh "go vet"
                     sh "go run -race ."
                     sh "go test"
               }
          }
          stage("Build && Sonarqube analysis") {
               steps {
                    withSonarQubeEnv('SonarQube Server') {
                    sh "go build"
               }
               }
          }
     }
}
