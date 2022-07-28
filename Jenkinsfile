pipeline{
    stages{
        stage('source code '){
            steps{
                git branch: 'main', url: 'https://github.com/Akshay0570/k8s-activity2.git'
            }
        }
        stage('image build'){
            steps{
                sh '''docker image build -t ak:57 .
docker image tag ak:57 akshay0570/ak:0570'''
            }
        }
        stage('push image to dockerhub'){
             steps{
            // This step should not normally be used in your script. Consult the inline help for details.
withDockerRegistry(credentialsId: 'docker', url: 'https://hub.docker.com/') {
    // some block
}
sh '''sudo docker login -u akshay0570 -p Akshay3578
docker push akshay0570/ak:0570'''
        }
        }
       stage('initializing k8s cluser'){
        steps{
            kubernetesDeploy configs: '.kube/config', dockerCredentials: [[credentialsId: 'docker', url: 'https://hub.docker.com/']], enableConfigSubstitution: false, kubeConfig: [path: ''], kubeconfigId: 'kubernetes', secretName: '', ssh: [sshCredentialsId: '*', sshServer: ''], textCredentials: [certificateAuthorityData: '', clientCertificateData: '', clientKeyData: '', serverUrl: 'https://']
        }
       }
       stage('deployment and service'){
        
       }
    }
}