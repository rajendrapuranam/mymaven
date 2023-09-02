node('built-in')
{
    stage('ContinousDownload') 
    {
     git 'https://github.com/intelliqittrainings/maven.git'
    }
     stage('ContinousBuild') 
    {
     sh 'mvn package'
    }
    stage('ContinousDeployment') 
    {
     deploy adapters: [tomcat9(credentialsId: '8ae5d9a8-b744-4117-ad1e-121279543b65', path: '', url: 'http://172.31.33.43:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinousTesting') 
    {
     git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
    
     sh 'java -jar  /var/lib/jenkins/workspace/Scriptedpipeline1/testing.jar'
    }
    stage('ContinousDelivery')
    {
       deploy adapters: [tomcat9(credentialsId: '8ae5d9a8-b744-4117-ad1e-121279543b65', path: '', url: 'http://172.31.37.43:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
        
    
}
    

 
