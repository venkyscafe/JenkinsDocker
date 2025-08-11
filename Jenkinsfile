node('DOTNETCORE'){
	stage('SCM'){
		checkout([
            $class: 'GitSCM', 
            branches: [[name: '*/main']], 
            doGenerateSubmoduleConfigurations: false, 
            extensions: [], 
            submoduleCfg: [], 
            userRemoteConfigs: [[url: 'https://github.com/venkyscafe/JenkinsDocker']]])
	}
	stage('Build'){
        sh 'dotnet build ConsoleApp2'
		// try{
		// sh 'dotnet build ConsoleApp2'
		// }finally{
		// 	archiveArtifacts artifacts: 'ConsoleApp2/*.*'
		// }
	}
	stage('Test'){
		echo 'Execute unit tests'
        sh 'dotnet test ConsoleApp2'
	}
	stage('Package'){
		echo 'Zip it up'
        sh 'dotnet publish ConsoleApp2 -c Release -o out'
        archiveArtifacts artifacts: 'ConsoleApp2/out/**/*.*'
	}
	stage('Deploy'){
		echo 'Push to deployment'
	}
	stage('Archive'){
        archiveArtifacts artifacts: 'ConsoleApp2/bin/Debug/net6.0/**/*.*'
		// archiveArtifacts artifacts: 'ConsoleApp2/*.*'
	}	
}