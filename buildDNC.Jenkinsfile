def dockerImage;

node('docker'){
	stage('SCM'){
		checkout([
            $class: 'GitSCM', 
            branches: [[name: '*/main']], 
            doGenerateSubmoduleConfigurations: false, 
            extensions: [], 
            submoduleCfg: [], 
            userRemoteConfigs: [[url: 'https://github.com/venkyscafe/JenkinsDocker']]]);
	}
	stage('build'){
		dockerImage = docker.build('v3nkys/agent-dnc:v' + env.BUILD_NUMBER, '.');
	}
	stage('push'){
		docker.withRegistry('https://index.docker.io/v1/', 'dockerhubcreds'){
			dockerImage.push();
		}
	}
}