pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/2025sl93012/labsheet1-2025sl93012.git'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Build Stage Running"'
            }
        }

        stage('Test') {
            steps {
                sh '''
                echo "Running Test Cases..."

                python3 <<EOF
from calculator import add, subtract, multiply, divide

assert add(2, 3) == 5
assert add(-1, 1) == 0

assert subtract(5, 3) == 2
assert subtract(0, 4) == -4

assert multiply(3, 4) == 12
assert multiply(-2, 3) == -6

assert divide(10, 2) == 5
assert divide(5, 0) is None

print("All test cases passed successfully!")
EOF
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh  '''
        scp -o StrictHostKeyChecking=no -i /var/lib/jenkins/key_2.pem calculator.py ec2-user@ec2-13-62-19-253.eu-north-1.compute.amazonaws.com:/home/ec2-user
        '''
            }
        }
    }
}

