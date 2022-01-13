def pipelineContext = [:]
node {

   def registryProjet='b.roussel-paille@ecole-ipssi.net/'
   def IMAGE="${registryProjet}apache:version-${env.BUILD_ID}"

    stage('Clone') {
          checkout scm
    }

    def img = stage('Build') {
          docker.build("$IMAGE",  '.')
    }

    stage('Run') {
          img.withRun("--name run-$BUILD_ID -p 8000:80") { c ->
       
          }
    }

    stage('Push') {
          docker.withRegistry('https://b.roussel-paille@ecole-ipssi.net', 'registry_id') {
              img.push 'latest'
              img.push()
          }
    }

}

