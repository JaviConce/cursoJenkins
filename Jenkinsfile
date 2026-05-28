pipeline {
    agent any

    parameters {
        booleanParam(name: 'BORRAR_ARCHIVOS', defaultValue: false, description: 'Si es true, elimina los archivos .txt generados')
    }

    stages {
        stage('EJercicio 1') {
            steps {
                script {
                    sh """
                        cat > saludo.txt << EOF
Hola Jenkins
EOF

                        echo "=== Contenido del archivo ==="
                        cat saludo.txt
                    """
                }
            }
        }
        stage ('EJercicio 2') {
            steps {
                script {
                    sh """
                        cat > datos.txt << EOF
Job:   ${env.JOB_NAME}
Build: ${env.BUILD_NUMBER}
Fecha: \$(date)
EOF
                        echo "=== Contenido del archivo ==="
                        cat datos.txt
                    """
                }
            }   
        }
        stage ('EJercicio 3') {
            stages {
                stage('Leer') {
                    steps {
                        script {
                            sh """
                                cat > info.txt << EOF
                                hola mundo
                                EOF
                            """
                        }
                    }
                }
                stage('Mostrar contenido') {
                    steps {
                        script {
                            sh """
                                echo "=== Contenido del archivo ==="
                                cat info.txt
                            """
                        }
                    }
                }
                stage('Borrar'){
                    steps {
                        script {
                            sh """
                                rm info.txt
                                echo "Archivo info.txt eliminado"
                            """
                        }
                    }
                }
            }
        }
        stage ('EJercicio 4') {
            steps {
                script {
                    NOMBRE="Javier de la COncepcion Dorado"
                    sh """
                        cat > nombre.txt << EOF
                        ${NOMBRE}
                        EOF
                    """
                    echo "=== Contenido del archivo ==="
                    sh "cat nombre.txt"
                }
            }
        }
        stage ('EJercicio 5') {
            steps {
                script {
                    sh """
                        touch uno.txt
                        touch dos.txt
                        touch tres.txt
                        ls -al
                    """
                }
            }
        }
        stage ('Borrar archivos') {
            steps {
                script {
                    sh """
                        rm -f *.txt
                        echo 'Archivos .txt eliminados'
                    """
                }
            }
        }
        stage ('EJercicio 6') {
            stages {
                stage ('Deploy') {
                    when {
                        branch 'main'
                    }
                    steps {
                        script {
                            sh """
                                echo "Simulando despliegue..."
                                sleep 2
                                echo "Despliegue completado"
                            """
                        }
                    }
                }
            }
        }
        stage ('EJercicio 7') {
            when {
                expression { params.BORRAR_ARCHIVOS }
            }
            steps {
                script {
                    sh """
                        rm -rf *.txt
                    """
                }
            }
        }
        stage ('EJercicio 8') {
            steps {
                script {
                    sh """
                        if [ -f config.txt ]; then
                            echo "config.txt existe"
                        else
                            echo "config.txt NO existe"
                        fi
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