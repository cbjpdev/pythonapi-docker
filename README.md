kind: BuildConfig
apiVersion: build.openshift.io/v1
metadata:
  name: py-api-docker
  namespace: myproject
spec:
  nodeSelector: null
  output:
    to:
      kind: ImageStreamTag
      name: 'py-api:latest'
  postCommit: {}
  resources: {}
  runPolicy: Serial
  source:
    git:
      ref: master
      uri: 'https://github.com/cbjpdev/pythonapi-docker.git'
    type: Git
  strategy:
    dockerStrategy:
      from:
        kind: DockerImage
        name: 'ubuntu:16.04'
    type: Docker
