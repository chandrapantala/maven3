pipeline
{
    agent any
    stages
    {
        stage('contdow')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('contbuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('contdepoly')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '940cfe09-3905-4644-be26-658311726026', path: '', url: 'http://172.31.7.4:8080')], contextPath: 'test11', war: '**/*.war'
            }
        }
        stage('conttest')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/dcl1@2/testing.jar'
            }
        }
        stage('contdel')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '93979f6a-0609-4aec-a5c4-bae15886e608', path: '', url: 'http://172.31.14.232:8080')], contextPath: 'prod11', war: '**/*.war'
            }
        }
    }
}
