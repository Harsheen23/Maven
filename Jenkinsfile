pipeline {
agent any // Use any available agent
tools {
maven 'Maven' // Ensure this matches the name configured in Jenkins
}
stages {
stage('Checkout') {
steps {
git branch: 'master', url:
'https://github.com/Harsheen23/Maven.git'
}
}
stage('Build') {
steps {
sh 'mvn clean package' // Run Maven build
}
}
stage('Test') {
steps {
sh 'mvn test' // Run unit tests
}
}
stage('Run Application') {
steps {
// Start the JAR application
sh 'java -jar target/MyMavenJenkinsPipeline-1.0-SNAPSHOT.jar'
}
}
stage('Archive') {
steps {
archiveArtifacts artifacts: 'target/*.war', fingerprint: true
}
}
stage('Deploy') {
steps {
sh 'mvn clean package'
}
}
}
post {
success {
echo 'Build and deployment successful!'
}
failure {
echo 'Build failed!'
}
}
}
