# Pod(파드)

- https://kubernetes.io/docs/concepts/workloads/pods/
- https://subicura.com/k8s/guide/pod.html

- Pod는 쿠버네티스에서 관리하는 가장 배포 단위
- Pod는 한 개 또는 여러 개의 컨테이너를 포함함
- 파드의 컨텍스트 내에서 개별 애플리케이션은 추가적으로 하위 격리가 적용됨


## Workload resources for managing pods

- 일반적으로 pod를 직접 만들 필요가 없음
- deployment 또는 job과 같은 워크로드 리소스를 사용하여 pod를 생성
- pod 상태를 추적해야 한다면 StatefulSet 리소스를 고려해야함

- 싱글 컨테이너 파드와 멀티 컨테이너 파드로 구분 할 수 있음


## Pod Template

- pod를 생성하기 위한 명세
- deployment, job, demonset과 같은 워크로드 리소스에 포함됨
- 파드 템플릿을 수정하거나 새로운 파드 템플릿으로 바꿔도 이미 존재하는 파드에는 직접적인 영향을 주지 않음
- 동작 중인 파드의 필드를 갱신하는 것이 가능하지만, patch 및 replace와 같은 파드 갱신 작업에는 제약이 있음 

## Resource sharing and communication


### Pod Storage

- 공유 스토리지 볼륨을 지정할 수 있음
- 파드의 모든 컨테이너는 공유 볼륨에 접근할 수 있고, 데이터를 공유할 수 있음
- 영구 데이터를 유지하도록 허용함

### Pod Networking

- 각 파드에는 고유한 ip 주소가 할당됨
- 파드의 모든 컨테이너는 네트워크 네임스페이스를 공유함
- 파드 내의 컨테이너간에는 localhost를 통해서 찾을 수 있고, IPC도 가능함
- 다른 파드 컨테이너는 OS 수준의 IPC로 통신이 불가능함


## Static Pods
- API 서버가 담당하지 않고, 특정 노드의 kubelet 데몬에서 직접적으로 관리되는 pod
- 대부분의 pod는 control plane에서 관리하는 반면에 static pod는 kubelet에서 직접 관리함

## Container probes
- kubelet에서 주기적으로 수행하는 진단
    - ExecAction (컨테이너 런타임의 도움을 받아 수행)
    - TCPSocketAction (kubelet)
    - HTTPGetAction (kubelet)


## Pod가 생성되는 과정

1. Scheduler가 API Server를 감시하면서 할당되는 Pod가 있는지 확인함
2. Scheduler는 할당되지 않은 Pod를 감지하고 적절한 노드에 할당함 
3. 노드에 설치된 kubelet이 자신의 노드에 할당된 Pod가 있는지 확인
4. kubelet은 Scheduler에 의해 자신에게 할당된 Pod의 정보를 확인하고 컨테이너 생성
5. kubelet은 자신에게 할당된 Pod의 상태를 API Server에 전달  