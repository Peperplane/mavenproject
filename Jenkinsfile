




node('built-in') 
  {
    stage('ContinuousDownload')
    {
        git 'https://github.com/intelliqittrainings/maven.git'
        
    }
    stage('ContinuousBuild'){
        
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
       
       deploy adapters: [tomcat9(credentialsId: '8d334f05-a0ae-4308-add0-3d0401f99e19', path: '', url: 'http://172.31.12.89:8080')], contextPath: 'testapp', war: '**/*.war'
        
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline1/testing.jar'
    }
    stage('ContinuousDelivery')
    {
        deploy adapters: [tomcat9(credentialsId: 'd79c5407-3b5e-4355-9bf2-4a1de40dd026', path: '', url: 'http://172.31.1.221:8080')], contextPath: 'prodapp', war: '**/*.war'        
    }
  }
