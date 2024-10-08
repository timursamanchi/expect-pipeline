pipeline {
    agent any
    stages {
        stage ('Initialize') {
            steps {
                echo "Initializing DB2 build"
                script {
                    // Initialize an empty array (List)
                    def testArray = []

                    // Add initial content to the array
                    testArray << "Pipeline build report"
                    testArray << "====================="
                    testArray << "=Build ${Build_Id}"

                    // Save the array for other stages
                    env.testArray = testArray.join('\n')
                }
            }
        }
    }
}