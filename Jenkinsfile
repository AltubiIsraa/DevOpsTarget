pipeline{
        agent any

		parameters {
  		 choice choices: ['qa', 'production'], description: 'Select environment for deployment', name: 'DEPLOY_TO'
 		 buildSelector defaultSelector: upstream(), name: 'BUILD_SELECTOR'
		}
    stage('Copy artifact') {
      steps {
        copyArtifacts filter: 'sample1', fingerprintArtifacts: true,
          projectName: "sample-multibranch/${params.upstreamJobName}", selector: upstream()
      }
    }
    stage('Deliver') {
      steps {
        sshagent(['vagrant-private-key']) {
          sh 'ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i ${DEPLOY_TO}.ini playbook.yml'
        }
      }
//            stages{
// 		  stage('Copy artifact'){
//                 steps{
// 			 copyArtifacts filter: 'sample1', fingerprintArtifacts: true, projectName: 'sample', selector: BUILD_SELECTOR
//                }
// }
			   
//              stage('Deliver'){
//               steps{
// 		sshagent(['vagrant-private-key']){
// 		  sh 'ansible-playbook --private-key=${keyfile} -i ${DEPLOY_TO}.ini playbook.yml'}
// 			}
//                }
            }
        }
