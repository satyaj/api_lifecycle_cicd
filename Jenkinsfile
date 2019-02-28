apiVersion: build.openshift.io/v1
kind: BuildConfig
metadata:
  creationTimestamp: '2019-02-28T14:39:25Z'
  labels:
    name: pipeline-build
  name: echo-user05-pipeline-build
  namespace: microcks
  resourceVersion: '99569581'
  selfLink: >-
    /apis/build.openshift.io/v1/namespaces/microcks/buildconfigs/echo-user05-pipeline-build
  uid: a5184f18-3b66-11e9-88dd-84349711e540
spec:
  failedBuildsHistoryLimit: 5
  nodeSelector: {}
  output: {}
  postCommit: {}
  resources: {}
  runPolicy: Serial
  source:
    type: None
  strategy:
    jenkinsPipelineStrategy:
      env:
        - name: GIT_BRANCH
          value: master
        - name: GIT_REPO
          value: 'https://github.com/satyaj/api_lifecycle_cicd'
      jenkinsfile: |-
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
    type: JenkinsPipeline
  successfulBuildsHistoryLimit: 5
  triggers:
    - type: ConfigChange
status:
  lastVersion: 12
