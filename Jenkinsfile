pipeline {
 environment {
 imagename = “adithyak21/jenkins-docker”
 registryCredential = ‘adithya-docckerhub’
 dockerImage = ‘’
 }
 agent any
 stages {
 stage(‘Cloning Git’) {
 steps {
 git([url: ‘https://github.com/abiola911/simple-docker.git', branch: ‘main’])
 }
 }
 stage(‘Building image’) {
 steps{
 script {
 dockerImage = docker.build simpledocker
 }
 }
 }
 stage(‘Running image’) {
 steps{
 script {
 sh “docker run emjay888/simpledocker:latest”
 }
 }
 }
 stage(‘Deploy Image’) {
 steps{
 script {
 docker.withRegistry( ‘’, registryCredential ) {
 dockerImage.push(“$BUILD_NUMBER”)
 dockerImage.push(‘latest’)
 }
 }
 }
 }
 }
}
