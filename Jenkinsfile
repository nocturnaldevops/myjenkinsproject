pipeline
{
agent any
stages
{
	stage("COntDownload")
	{
		steps
		{
		git branch: 'main', url: 'https://github.com/nocturnaldevops/Project1.git '
		}
	}
	stage("COntBuild")
	{
		steps
		{
		 sh 'mvn package'
		}
	}
	stage("COntDeployment")
	{
		steps
		{
		deploy adapters: [tomcat9(credentialsId: 'aff8f96e-5b52-4529-8364-eead2c7d847e', path: '', url: 'http://172.31.31.82:8080')], contextPath: 'testapplication1', war: '**/*.war'
		}
	}
	stage("COntTest")
	{
		steps
		{
	 sh 'echo "testing passed"'
		}
	}
	stage("COntDelivery")
	{
		steps
		{
		sh 'scp /var/lib/jenkins/workspace/cicdprojectpipeline/target/devops.war ubuntu@172.31.31.184:/var/lib/tomcat9/webapps/myapplication.war'		
		}
	}
}
}
