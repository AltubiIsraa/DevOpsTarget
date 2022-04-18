pipeline{
        agent any
           stages{
		  stage('Copy artifact'){
                steps{
			 copyArtifacts filter: 'sample1', fingerprintArtifacts: true, projectName: 'sample', selector: lastSuccessful()
               }
}
              stage('Deliver'){
                steps{
			withCredentials([sshUserPrivatekey(credentialsId: "vagrant-private-key", keyFileVariable: 'keyfile')]){
                    sh 'scp -i ${keyfile}./sample1 vagrant@10.10.50.3'

			}
               }
            }
        }
}