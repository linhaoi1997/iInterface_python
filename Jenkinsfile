library 'qa-pipeline-library' 


pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Build"
                export LANG=zh_CN.utf8
                source venv/bin/activate
                cd iInterface_python
                pip install -r requirements.txt
            }
        }
        stage('Test') {
            steps {
               echo "Test"
               pytest -sv test/weather_test.py --alluredir ./allure-results
            }
        }
        stage('统计数据') {
            steps {
                echo "统计数据"
                saveReportToDB()
            }
        }
    }
}








