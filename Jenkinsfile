pipeline {
    agent any

    stages {

        stage('Crear Archivo') {
            steps {
                script {
                    sh """
                        cat > hola.txt << EOF
Hola Jenkins
Job:   ${env.JOB_NAME}
Build: ${env.BUILD_NUMBER}
Fecha: \$(date)
EOF
                        echo "=== Contenido del archivo ==="
                        cat hola.txt
                    """
                }
            }
        }

    }

    post {
        success {
            echo "✅ Archivo creado correctamente"
        }
    }
}