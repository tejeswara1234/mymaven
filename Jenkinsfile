pipeline
{
    agent any
    stages
    {
        stage('ConDownload')
        {
            steps
            {
               git 'https://github.com/intelliqittrainings/maven.git' 
            }
        }
         stage('ConBuild')
        {
            steps
            {
                sh 'mvn package' 
            }
        }
        stage('ConDeployment')
        {
            steps
            {
                 deploy adapters: [tomcat9(credentialsId: 'b6c88c11-0b67-4774-a6f1-28a76f022dca', path: '', url: 'http://172.31.5.126:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage('ConTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DecalrativePipeline1/testing.jar'
            }
        }
        stage('ConDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'b6c88c11-0b67-4774-a6f1-28a76f022dca', path: '', url: 'http://172.31.5.55:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
         
    }
}

