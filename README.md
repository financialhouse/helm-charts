# Financialhouse helm chart repository

This repository will host the base helm charts for financialhouse

## Creating a new chart

* Go to charts directory and create a new chart:

  ```
  cd charts && helm create test
  ```

* Package the chart which created earlier:

  ```
  in the root folder of the repository run:

  helm package charts/test
  ```

## Update and publish index.yaml file

* In the root folder run:

  ```
  helm repo index --url https://financialhouse.github.io/helm-charts --merge index.yaml .
  ```

* Check the index.yaml file. Should look something like this:

  ```
    cat index.yaml ->

    apiVersion: v1
  entries:
    app:
    - apiVersion: v2
      appVersion: v0.0.1
      created: "2022-05-24T13:07:21.090051+02:00"
      description: Base Helm Chart for Financialhouse frontend and backend applications.
      digest: 1873dc98d5b3a1c6bcba7ebf3ce381bd422b329e588b870095270ea36aa4e828
      name: app
      type: application
      urls:
      - https://financialhouse.github.io/helm-charts/app-v0.0.1.tgz
      version: v0.0.1
    test:
    - apiVersion: v2
      appVersion: 1.16.0
      created: "2022-05-24T13:07:21.090408+02:00"
      description: A Helm chart for Kubernetes
      digest: 949f27e346a18e4a802bfde1870647bd9572386c655ecaaf7b67e813d5dd2859
      name: test
      type: application
      urls:
      - https://financialhouse.github.io/helm-charts/test-0.1.0.tgz
      version: 0.1.0
  generated: "2022-05-24T13:07:21.089485+02:00"
  ```

* Push changes

## Host to use the helm chart repository

* First add the repository localy

  ```
  helm repo add financialhouse https://financialhouse.github.io/helm-charts/
  ```
* Update repositories

  ```
  helm repo update
  ```

* Install desired helm chart from the repository

  ```
  helm upgrade --install my-chart financialhouse/test
  ```


> **_NOTE:_** Don't forget to update repositories localy once you add a new helm chart

```
helm repo update
```
