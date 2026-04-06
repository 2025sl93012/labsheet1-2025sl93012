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

assert add(7, 6) == 13
assert add(1, 2) == 3

assert subtract(6, 7) == -1
assert subtract(1, 4) == -3

assert multiply(3, 1) == 3
assert multiply(-2, 5) == -10

assert divide(9, 3) == 3
assert divide(7, 0) is None

print("All test cases passed successfully!")
EOF
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo "Deploy Stage"'
            }
        }
    }
}
