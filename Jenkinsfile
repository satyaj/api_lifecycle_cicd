
          stage('Ansible Galaxy')  {
            sh "ansible-galaxy install nmasse-itix.threescale-cicd"
          }
          stage('Ansible Deploy')  {
            ansiColor('xterm') {
              ansiblePlaybook(
                playbook: 'deploy-api.yaml',
                inventory: 'inventory',
                colorized: true)
            }
          }

