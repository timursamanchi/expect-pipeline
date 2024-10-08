pipeline {
    agent any
    stages {
        stage ('Initialize') {
            steps {
                echo "Initializing DB2 build"
                script {
                    // Initialize an empty array (List)
                    def textArray = []

                    // Add initial content to the array
                    textArray << "Pipeline build report"
                    textArray << "====================="
                    textArray << "=Build ${BUILD_ID}"

                    // Save the array as a string for other stages
                    env.textArray = textArray.join('\n')
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    // Simulate output from the build stage
                    def buildOutput = "Build ${BUILD_ID} output: Successfully compiled!"
                    echo buildOutput

                    // Retrieve the array (currently stored as a string) and convert it back into a List
                    def textArray = env.textArray.split("\n") as List

                    // Append new build output to the array
                    textArray << "Build ${BUILD_ID} - Completed successfully!"

                    // Convert the list back into a string and store it in env
                    env.textArray = textArray.join('\n')
                }
            }
        }
        stage('Generate Report') {
            steps {
                script {
                    // Retrieve the final array from the environment variable
                    def textArray = env.textArray.split("\n") as List

                    // Create the report by joining the array into a string
                    def reportContent = textArray.join('\n')

                    // Write the report to a file
                    def reportFile = "report.txt"
                    writeFile(file: reportFile, text: reportContent)

                    // Archive the report as an artifact
                    archiveArtifacts artifacts: reportFile
                }
            }
        }
    }
}
