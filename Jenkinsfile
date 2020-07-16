podTemplate(
    cloud: 'sgh-lsg-ibm',
    containers: [
    containerTemplate( name: 'nodejs', image: 'openshift/jenkins-agent-nodejs-8-centos7', ttyEnabled: true, command: 'cat')
  ]) {

    node(POD_LABEL) {
        stage('nodejs') {
            git 'https://github.com/asialogi/web-nodejs-sample.git'
            container('nodejs') {
                stage('build') {
                    sh 'npm install'
                }
                stage('code-coverage') {
                    sh 'node sonar-project.js'
                }
            }
        }
    }
}