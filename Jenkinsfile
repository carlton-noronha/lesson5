node('master') {
    stage("Fetch Source Code") {
    	cleanWs()
        git([url: 'https://github.com/carlton-noronha/lesson5.git', branch: 'functions-and-tests'])
    }
    
    dir('.') {
        printMessage('Running Pipeline')
        stage("Testing") {
	    sh 'ls -la'
	    sh 'apk add python3'
            sh 'python3 test_functions.py'
        }
        stage("Deployment") {
            if (env.BRANCH_NAME == 'main') {
                printMessage('Deploying the master branch')
            } else {
                printMessage("No deployment for branch [${env.BRANCH_NAME}]")
            }
            
        }
        printMessage('Pipeline Complete')
    }
}

def printMessage(message) {
    echo "${message}"
}
