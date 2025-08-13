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
		docker.withRegistry('https://index.docker.io/v1/', 'dockerhubcreds') {
			sh 'docker buildx create --name v3nkyscafe'
			sh 'docker buildx use v3nkyscafe'
			sh 'docker buildx build -t v3nkys/simplednc:jenkins --platform=linux/amd64,linux/arm/v7 --push -f dngit.Dockerfile .'
		}
	}
}