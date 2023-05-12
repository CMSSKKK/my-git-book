# Kubernetes Components

- https://kubernetes.io/docs/concepts/overview/components/

![components](https://github.com/CMSSKKK/my-git-book/assets/81129309/efc0601a-e880-49cc-9849-59441cb8408a)

- 쿠버네티스를 배포하면, 클러스터를 가지게 됨
- 쿠버네티스 클러스터는 컨테이너라이징된 애플리케이션을 실행하는 노드(워커 머신)들로 구성됨
- 모든 클러스터는 적어도 하나의 워커 노드를 가지고 있음
- 워커 노드들은 애플리케이션 워크로드의 구성요소인 Pods를 호스팅함
- control plane은 워커 노드와 클러스터 내의 Pods를 관리함
- 프로덕션 환경에서 control plane은 일반적으로 여러 컴퓨터에서 실행되고, 클러스터는 일반적으로 여러 노드를 실행하여 내결함성과 고가용성을 제공함

## Control Plane Components 

- control plane의 컴포넌트들은 클러스터에 대한 전역적인 결정(예를 들어, 스케줄링)을 내림
- 또한 클러스터의 이벤트를 감지하고 응답함
- Control plane은 클러스터 내의 어떠한 머신에서도 작동할 수 있음
- 하지만, 간단하게 하기위해서 일반적으로 동일한 머신에 control plane 컴포넌트를 시작하고, 이 머신에서 사용자 컨테이너를 실행하지 않음

### Kube-apiserver
- control plane의 앞단
- 수평으로 확장되도록 디자인
- 여려 인스턴스를 실행하고 인스턴스간의 트래픽의 균형을 맞출 수 있음

### etcd
- 모든 클러스터 데이터에 대한 Kubernetes의 백업 저장소로 사용되는 일관되고 가용성이 높은 키 값 저장소
- etcd를 백업 저장소로 사용한다면, 데이터 백업 전략을 확인해야함

### kube-scheduler
- 새로 생성된 Pod을 감지하고 실행할 노드를 선택

### kube-controller-manager
- controller process를 실행하는 컴포넌트
- 별도의 프로세스이지만, 복잡성을 줄이기 위해서 모두 단일 바이너리로 컴파일되고 단일 프로세스에서 실행됨 

### cloud-controller-manager
