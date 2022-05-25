pipeline {
    agent any
    stages {
        stage("Compile") {
            steps {
                sh "./gradlew compileJava"
            }
        }
        stage ("Unit test") {
            steps {
                sh "./gradlew test"
            }
        }
        stage ("Code Coverage") {
            steps {
                sh "./gradlew jacocotestReport"
                publishHTML (target: [
                    reportDir : "build/reports/jacoco/test/html",
                    reportFiles: "index.html",
                    reportName: "Jacoco Report"
                ])
                sh "./gradlew jacocotestCoverageVerification"
            }
        }
    }
}