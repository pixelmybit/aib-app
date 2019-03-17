@Library('pipeline-library-demo')_
def func1(String name ){
   echo "Hellow $name"
}
node('maven-label') { 
   def mvnHome
   stage("Welcome"){
   func1 "DevOps"
   }
    stage("sayHello"){
   sayHello "jbvjb"
}
   stage('Preparation') { 
      git 'https://github.com/cicd-tools2/aib-app.git'
            
      mvnHome = tool 'M3'
   }
   stage('Build') {
      
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
}
