
        node ('ansible') {
          def ansiblePlaybookExtraVars = [
            git_repo: params.GIT_REPO,
            git_branch: params.GIT_BRANCH,
          ]        
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
        }

