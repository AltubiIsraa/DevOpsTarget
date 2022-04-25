pipeline{
        agent any

		parameters {
  		 choice choices: ['qa', 'production'], description: 'Select environment for deployment', name: 'DEPLOY_TO'
		}

           stages{
		  stage('Copy artifact'){
                steps{
			 copyArtifacts filter: 'sample1', fingerprintArtifacts: true, projectName: 'sample', selector: lastSuccessful()
               }
}
             // stage('Deliver'){
               // steps{
		//	sshagent(['vagrant-private-key']){
		//		sh 'ansible-playbook --private-key=${keyfile} -i ${DEPLOY_TO}.ini playbook.yml'}
		//	}
              // }
            }
        }
}
