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
                    sh 'scp ./sample vagrant@10.10.50.3'
               }
            }
        }
}