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
	}
	stage('Package'){
		echo 'Zip it up'
	}
	stage('Deploy'){
		echo 'Push to deployment'
	}
	stage('Archive'){
		archiveArtifacts artifacts: 'ConsoleApp2/*.*'
	}	
}