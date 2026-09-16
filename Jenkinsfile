pipeline {
    agent any

    stages {
        stage("Checkout") {
            steps {
                echo "Obteniendo el codigo del repositorio..."
                checkout scm
            }
        }
        stage("Instalacion de dependencias") {
            steps {
                bat "\"C:\\Users\\Usuario\\AppData\\Local\\Python\\bin\\python.exe\" -m pip install --upgrade pip"
                bat "\"C:\\Users\\Usuario\\AppData\\Local\\Python\\bin\\python.exe\" -m pip install -r requirements.txt"
            }
        }
        stage("Pruebas basicas") {
            steps {
                bat "\"C:\\Users\\Usuario\\AppData\\Local\\Python\\bin\\python.exe\" -m pytest tests/"
            }
        }
        stage("Ejecucion del pipeline de AG") {
            steps {
                bat "\"C:\\Users\\Usuario\\AppData\\Local\\Python\\bin\\python.exe\" main.py"
            }
        }
    }

    post {
        always {
            echo "Archivando metricas y graficas..."
            archiveArtifacts artifacts: "outputs/*", allowEmptyArchive: true
        }
    }
}
