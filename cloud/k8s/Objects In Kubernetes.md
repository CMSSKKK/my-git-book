# Objects In Kubernetes

- https://kubernetes.io/docs/concepts/overview/working-with-objects/

## Kubernetes objects 
- 쿠버네티스 시스템에 있는 영구적인 엔티티
- 쿠버네티스는 objects를 사용해서 클러스터의 상태를 표현함
-----
- 동작중인 컨테이너라이징된 애플리케이션
- 해당 애플리케이션에 사용 가능한 자원
- 재시작, 업그레이드 및 내결함성과 같은 작동 방식에 대한 정책
----
- kubernetes objects는 한번 생성한 오브젝트들에 대한 의도의 기록들임, 쿠버네티스 시스템은 오브젝트가 존재하는지 확인하기 위해서 지속적으로 작동함
- kubernetes objects로 작업을 하려면, kubernetes API를 사용해야 함

## Object spec and status

- 거의 모든 Kubernetes object에는 구성을 관리하는 두 개의 중첩된 object 필드(spec 및 status)가 포함되어 있음

## Describing a kubernetes objects

- Kubernetes API를 사용하여 객체를 생성하는 경우, API 요청에는 해당 정보가 요청 본문에 JSON으로 포함되어야 함
- 대부분 kubectl로 .yaml 파일로 전달함
- kubectl이 해당 정보를 JSON으로 변환함


## Required fields

- `apiVersion` : 사용하고자하는 Kubernetes API version
- `kind` : 생성하고자하는 오브젝트의 종류
- `metadata` : 오브젝트를 유일하게 식별할 수 있도록 돕는 정보 (`name`, `UID`, `namespace`)
- `spec` : object의 원하는 상태


## Example
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  selector:
    matchLabels:
      app: nginx
  replicas: 2 # tells deployment to run 2 pods matching the template
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```