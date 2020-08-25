
pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        
        stage('build') {
            steps {
                echo 'Hello build'
                sh 'mvn clean'
                sh 'mvn install'
                sh 'mvn package'
            }
        }
        
        stage('deploy') {
            steps {
                echo 'Hello deploy'
            }
        }
        
        stage('build and push image') {
            steps {
              script {
                  checkout scm
                  docker.WithRegistry('', 'dockerUserID') {
                  def customImage = docker.build("bkamche/devops-pipeline:${env.BUILD_ID}")
                  customImage.push()
                
            }
        }
    }
}

