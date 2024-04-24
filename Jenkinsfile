pipeline {
    agent any

    options {
         timeout(time:5, unit: 'MINUTES')
    }

    environment {
        // Variables de entorno
        NUM1 = 10
        NUM2 = 5
    }

    stages {
        stage('Operaciones Aritméticas') {
            steps {
                script {
                    // Operaciones aritméticas básicas
                    suma = env.NUM1.toInteger() + env.NUM2.toInteger()
                    resta = env.NUM1.toInteger() - env.NUM2.toInteger()
                    multiplicacion = env.NUM1.toInteger() * env.NUM2.toInteger()
                    division = env.NUM1.toInteger() / env.NUM2.toInteger()

                    // Imprimir los resultados en la consola
                    echo "Suma: ${suma}"
                    echo "Resta: ${resta}"
                    echo "Multiplicación: ${multiplicacion}"
                    echo "División: ${division}"
                }
            }
        }

        stage('Flush DNS Cache') {
            steps {
                // Ejecutar un comando de Windows
                bat 'ipconfig /flushdns'
            }
        }

        stage('Generar Archivo TXT') {
            steps {
                script {
                    // Generar un archivo de texto con la información de las operaciones
                    writeFile file: 'resultado_operaciones.txt', text: """\
                    Suma: ${suma}
                    Resta: ${resta}
                    Multiplicación: ${multiplicacion}
                    División: ${division}
                    """
                    echo "Archivo generado: resultado_operaciones.txt"
                }
            }
        }
    }

    post {
        always {
            echo 'Este mensaje siempre se mostrará, sin importar el resultado del pipeline.'
        }
        success {
            echo 'El pipeline se ejecutó exitosamente.'
        }
        failure {
            echo 'El pipeline falló.'
        }
    }
}
