node("built-in")
{
    stage('continous download')
    {
        try
        {
            git'https://github.com/ajayhp07/maven.git'
        }
        catch(Exception e)
        {
            mail bcc: '', body: 'download error', cc: '', from: '', replyTo: '', subject: 'download failed', to: 'ajjuhp783@gmail.com'
        
            exit(1)
        }
    }
    stage('continous build')
    {
        try
        {
            sh'mvn package'
        }
        catch(Exception e2)
        {
            mail bcc: '', body: 'build error', cc: '', from: '', replyTo: '', subject: 'build failed', to: 'ajjuhp783@gmail.com'
        
            exit(1)
        }
    }
    stage('continous deploy')
    {
        try
        {
            sh'scp /var/lib/jenkins/workspace/scripted/webapp/target/webapp.war ubuntu@172.31.16.43:/var/lib/tomcat9/webapps/qa.war'
        }
    
        catch(Exception e3)
        {
            mail bcc: '', body: 'deploy error', cc: '', from: '', replyTo: '', subject: 'deploy failed', to: 'ajjuhp783@gmail.com'
        }
    }
    stage('continous test')
    {
        try
        {
            git'https://github.com/ajayhp07/Test.git'
            
            sh'java -jar /var/lib/jenkins/workspace/scripted/testing.jar '
        }
        catch(Exception e4)
        {
            mail bcc: '', body: 'test error', cc: '', from: '', replyTo: '', subject: 'test failed', to: 'ajjuhp783@gmail.com'
        }
    }
    stage('continous prod')
    {
        try
        {
            sh'scp /var/lib/jenkins/workspace/scripted/webapp/target/webapp.war ubuntu@172.31.29.33:/var/lib/tomcat9/webapps/aaa.war'        
        }
        catch(Exception e5)
        {
            mail bcc: '', body: 'prod error', cc: '', from: '', replyTo: '', subject: 'prod failed', to: 'ajjuhp783@gmail.com'
        }
    }
}
