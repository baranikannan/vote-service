#!groovy
@Library('jenkins-shared-library')
import com.sivalabs.JenkinsMavenLib

def dockerUsername = 'sivaprasadreddy'
def dockerImageName = 'vote-service'

def project = new JenkinsMavenLib(this, scm, env, params, currentBuild)

node {

    try {
        stage("Checkout") {
            project.checkout()
        }
        stage("setPermission") {
            sh '''
            ls -ltr
            chmod +x mvnw 
            '''
        }        
        stage("Build") {
            project.runTests()
        }
    }
    catch(err) {
        echo "ERROR: ${err}"
        currentBuild.result = currentBuild.result ?: "FAILURE"
    }
}
