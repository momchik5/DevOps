pipeline {
    agent any

    stages {
        stage('1. Подготовка окружения') {
            steps {
                echo 'Этап 1: Установка Docker, клонирование'
                ansiblePlaybook(
                    playbook: 'ansible/run_playbook.yml',
                    inventory: 'ansible/hosts',
                    tags: 'clone',
                    become: true,
                    colorized: true
                )
            }
        }
        
        stage('2. Запуск приложений') {
            steps {
                echo 'Этап 2: Запуск через Docker Compose'
                ansiblePlaybook(
                    playbook: 'ansible/run_playbook.yml',
                    inventory: 'ansible/hosts',
                    tags: 'start',
                    become: true,
                    colorized: true
                )
            }
        }
    }
}