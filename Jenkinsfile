pipeline{
    agent{
        node {
            label "python-agent"
        }
    }

    triggers {
       pollSCM '*/5 * * * *'
    }

    stages{
        stage("Build"){
            steps{
                echo "Building the application"
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                
                cd my-app
                pip install -r requirements.txt
                '''
            }
        }
        stage("Test"){
            steps{
                echo "Testing the application"
                sh '''
                . venv/bin/activate
                
                echo "Running without name"
                python3 my-app/hello.py
                
                echo "Running with name "
                python3 my-app/hello.py -name=Aradhya
                '''
            }
        }
        stage("Deliver"){
            steps{
                echo "Delivering the application"
                sh '''
                echo "Doing delivery stuff"
                '''
            }
        }
    }
}
