pipeline {
     agent any
     stages {
          tools {
               go 'default-go'
          }    
          stage("SCM Checkout") {
               steps {
                    git 'https://github.com/vishureddy/Jenkins_CI.git'
               }
          }
          stage("Pre-Test") {
               steps {
                    sh "go get -u golang.org/x/lint/golint"
                    sh "github.com/logrusorgru/aurora"
               }
          }
          stage("Testing") {
               steps {
                     sh "go fmt"
                     sh "golint"
                     sh "go vet"
                     sh "go run -race ."
                     sh "go test"
               }
          }
          stage("Build") {
               steps {
                    sh "go build"
               }
          }
     }
}