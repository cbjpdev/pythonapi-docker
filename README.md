apiVersion: build.openshift.io/v1
kind: BuildConfig
metadata:
  annotations:
    openshift.io/generated-by: OpenShiftWebConsole
  creationTimestamp: '2020-05-20T14:44:04Z'
  labels:
    app: py-api
  name: py-api-docker
  namespace: myproject
  resourceVersion: '70451'
  selfLink: /apis/build.openshift.io/v1/namespaces/myproject/buildconfigs/py-api
  uid: 5a06fc4e-9aa8-11ea-ad74-080027f01ead
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
        namespace: openshift
    type: Docker
  triggers:
    - imageChange:
        lastTriggeredImageID: >-
          172.30.1.1:5000/openshift/python@sha256:670363b3a2b4b740f452d2e2f26062c8cba7c4997a4411672b0e4b1a4d6b2ccc
      type: ImageChange
    - type: ConfigChange
    - generic:
        secret: 51598d872e6a05b9
      type: Generic
    - github:
        secret: 05ebe2de7395d189
      type: GitHub
status:
  lastVersion: 1
