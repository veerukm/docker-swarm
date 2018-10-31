node  ('prod'){
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build images') {
        /* This builds the actual image; synonymous to
         * docker build on the command line. */
             echo "${env.BUILD_NUMBER}"
             sh 'docker build -t linuxcloudops/website-test -f webpage .'
    }
    stage('Deploy ') {  
           
           /* sh " docker srevice create --name web -p 9089:80  linuxcloudops/website-test:${env.BUILD_NUMBER}"  */
             echo "linuxcloudops/website-test:${env.BUILD_NUMBER}"
             sh " sed -i 's/website-test/website-test:${env.BUILD_NUMBER}/g' docker-stack.yml"
             sh "docker stack deploy -c docker-stack.yml web" 
         }
   }   
