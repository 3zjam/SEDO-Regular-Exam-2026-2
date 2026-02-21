pipeline {
    agent any

    stages {
        stage("Restore dependencies") {
            when {
                expression {
                    return env.GIT_BRANCH?.endsWith('main')
                }
            }
            steps {
                bat "dotnet restore"
            }
        }

        stage("Build the project") {
            when {
                expression {
                    return env.GIT_BRANCH?.endsWith('main')
                }
            }
            steps {
                bat "dotnet build --no-restore"
            }
        }

        stage("Run the tests") {
            when {
                expression {
                    return env.GIT_BRANCH?.endsWith('main')
                }
            }
            steps {
                bat "dotnet test --no-build --verbosity normal"
            }
        }
    }
}