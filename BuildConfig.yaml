apiVersion: build.openshift.io/v1
kind: BuildConfig
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
      uri: "https://github.com/cbjpdev/pythonapi-docker.git"
    type: Git
  strategy:
    dockerStrategy:
      from:
        kind: DockerImage
        name: "ubuntu:16.04"
    type: Docker
  triggers:
    - 
      type: ImageChange
    - generic:
        secret: 51598d872e6a05b9
      type: Generic
    - github:
        secret: 05ebe2de7395d189
      type: GitHub
status:
  lastVersion: 1