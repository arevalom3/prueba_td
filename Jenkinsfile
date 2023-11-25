pipeline {
    agent any
    
    stages {
        stage('Clonar Repositorio') {
            steps {
                // Clona el repositorio de la aplicación desde el control de versiones de la rama principal con sus credenciales configuradas
                git branch: 'main', credentialsId: 'jenkins_llave_privada', url: 'https://github.com/arevalom3/prueba_td.git'
            }
        }
        
        stage('Instalar Dependencias') {
            steps {
                // Instala las dependencias de Node.js y de la aplicación React del repositorio clonado
                sh 'npm install'
            }
        }
        
        stage('Construir la Aplicación') {
            steps {
                // Construir la aplicación React
                sh 'npm run build'
            }
        }
		
		stage('Inicio de la Aplicación') {
            steps {
                // Inicia el servicio de la aplicación React
                sh 'npm install -g serve'
            }
        }
		
		stage('Ejecucion de la Aplicación') {
            steps {
                // Ejecuta la aplicación React
                sh 'serve -s build'
            }
        }
    }
    
    post {
        success {
            // accion: Si el despliegue es exitoso
            echo 'Despliegue exitoso'
        }
        failure {
            // accion: Si no realiza el despliegue
            echo 'Error en el despliegue'
        }
    }
}