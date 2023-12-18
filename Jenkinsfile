pipeline {
    agent any

    options {
        disableConcurrentBuilds(abortPrevious: true)
        timeout(activity: true, time: 10, unit: 'MINUTES')
    }

    tools {
        maven 'DEFAULT'
        jdk 'JDK 17 Adoptium'
    }

    parameters {
        booleanParam(
                name: 'skipTests',
                description: 'Skip tests',
                defaultValue: false
        )
    }

    stages {
        stage('Deploy') {
            steps {
                script {
                    sh "mvn -B clean deploy -P TPF -DskipTests=${params.skipTests}"
                }
            }
        }
    }
}
