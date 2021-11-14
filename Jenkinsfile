/* groovylint-disable NglParseError */
/* groovylint-disable-next-line NglParseError */
podTemplate(
   containers: [
        containerTemplate(image: 'docker', name: 'docker', command: 'cat', ttyEnabled: true),
        containerTemplate(name: 'eb', image: 'mini/eb-cli', command: 'cat', ttyEnabled: true)],
    volumes: [hostPathVolume(hostPath: '/var/run/docker.sock', mountPath: '/var/run/docker.sock')]) {
    node(POD_LABEL) {
        stage('fastforward master to staging') {
            properties([parameters([pipelineTriggers([cron('*/2 * * * *')]),])])

            sh 'pwd'
            sh 'git status'
            sh 'git checkout staging'
            sh 'git merge origin/master'
        }
    }
    }
