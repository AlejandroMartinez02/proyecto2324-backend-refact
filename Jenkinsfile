pipeline {
    agent any

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-amd64'
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Clonar Repositorio') {
            steps {
                echo 'Clonando el repositorio desde GitHub...'
                checkout scm
            }
        }

        stage('Compilar Proyecto') {
            steps {
                echo 'Compilando el proyecto...'
                sh 'mvn clean compile'
            }
        }

        stage('Ejecutar Tests') {
            steps {
                echo 'Ejecutando tests...'
                sh 'mvn test'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completado, limpiando el workspace...'
            cleanWs()
        }
        success {
            echo 'Pipeline ejecutado con éxito.'
        }
        failure {
            echo 'Pipeline falló en alguno de los pasos.'
        }
    }
}