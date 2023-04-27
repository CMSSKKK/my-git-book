# OpenStack

## LIBVIRT & QEMU/KVM

[https://www.youtube.com/watch?v=N5vnBdDOZ9g](https://www.youtube.com/watch?v=N5vnBdDOZ9g)

- kvm(가속기) + qemu(에뮬레이터) = VM
- libvirt : 가상머신을 관리하는 데몬 (xml 기반으로 관리)
    - virsh command - (api) - libvirt
    - xml(network, disk, cpu, memory)
- qemu → 자원(cpu, mem, disk)생성(관리기능이 없음) → 관리를 위해서 libvirt를 활용
- kvm의 경우 os 위에서 실행되는 것이 아니라, 리눅스커널의 일부(하이퍼바이저로 변환하는 것)
- VM(process) - TAP 디바이스 - 리눅스 브릿지 - iptables(nftables)
- libvirt 단점 : xml이 업데이트가 되면, 대부분 리부트가 되어야 한다.
- openstack → libvirt 기반
    - nova - compute가 장애가 생기면 virsh로 확인할 수 있다.

## Openstack (IaaS)

[01 클라우드 컴퓨팅과 공개 소프트웨어](https://www.youtube.com/watch?v=VOnGQVgZyO8&list=PLkgLtPJ7Lg3paDba9_z8m-VRGR88CFK67)

- 클라우드 환경에서 컴퓨팅 자원과 스토리지 인프라를 셋업하고 구동하기 위해 사용하는 오픈 소스 소프트웨어 프로젝트의 집합
- 클라우드 OS

![cloud os](https://user-images.githubusercontent.com/81129309/234818410-4ffa1800-948f-4f50-a0fe-83700acef7ec.png)

### 구조

![구조](https://user-images.githubusercontent.com/81129309/234818769-4cdb6f92-c99b-4656-a989-c4ea55ca5744.png)

- Nova-Compute
    - 구조
        - Nova - API(Proxy) 전달
            - Nova-Compute
                - LIBVIRT (가상화 라이브러리 데몬)
                    - QEMU
                    - KVM
    - 처리하는 자원
        - Flavor  - (Nova 내부)
        - Image  - (Glance)
        - Disk  - (Cinder)
        - Network  - Neutron
    
    - XML을 LIBVIRT에 전달