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
                    textArray << "=Build ${Build_Id}"

                    // Save the array for other stages
                    env.textArray = textArray.join('\n')
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    // Simulate output from the build stage
                    def buildOutput = "Build ${Build_Id} output: Successfully compiled!"
                    echo buildOutput

                }
            }
        } 
    }
}