pipeline{
        agent any

		parameters {
  		 choice choices: ['qa', 'production', 'staging'], description: 'Select environment for deployment', name: 'DEPLOY_TO'
 		 buildSelector defaultSelector: upstream(), name: 'BUILD_SELECTOR'
		}

           stages{
		  stage('Copy artifact'){
                steps{
			 copyArtifacts filter: 'sample1', fingerprintArtifacts: true, projectName: 'sample', selector: BUILD_SELECTOR
               }
}
		   
// 		   stages {
//    			 stage('Copy artifact') {
//     			  steps {
// 				copyArtifacts filter: 'sample1', fingerprintArtifacts: true,
//         			projectName: "sample-multibranch/${params.upstreamJobName}", selector: upstream()
// 			      }
//   				  }
			   
             stage('Deliver'){
              steps{
		sshagent(['vagrant-private-key']){
		  sh 'ansible-playbook --private-key=${keyfile} -i ${DEPLOY_TO}.ini playbook.yml'}
			}
               }
            }
        }
