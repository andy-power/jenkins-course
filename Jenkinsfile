
def app = "maven-code-coverage"  // This variable is global
node('small') {
    stage('Build') { // for display purposes
        def course = "jenkins-course"  // This variable is local to this stage
        git branch: 'main', url: "https://github.com/andy-power/${course}/"
        sh "mvn clean compile -f ${app}"

    }
    stage('Test') {
        sh "mvn clean test -f ${app}"

        // In scripted pipelines we don't have post actions!
        junit '**/target/surefire-reports/TEST-*.xml'
        jacoco buildOverBuild: true, deltaBranchCoverage: '80', deltaClassCoverage: '80', deltaComplexityCoverage: '80', deltaInstructionCoverage: '80', deltaLineCoverage: '80', deltaMethodCoverage: '80'
    }
}
