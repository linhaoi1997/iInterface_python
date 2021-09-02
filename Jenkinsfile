library 'allure_ statistics' 


pipeline {
    agent {label 'lin\'s mac'}
    stages {
        stage('Build') {
            steps {
                sh '''
                echo "Build"
                export LANG=zh_CN.utf8
                source venv/bin/activate
                cd iInterface
                pip install -r requirements.txt
                '''

            }
        }
        stage('Test') {
            steps {
               echo "Test"
               sh '''
               pytest -sv test/weather_test.py --alluredir ./allure-results
               '''
            }
        }
        stage('统计数据') {
            steps {
                echo "统计数据"
                allure includeProperties: false, jdk: '', results: [[path: 'iInterface/allure-results']]
                saveReportToDB()
            }
        }
    }
}








