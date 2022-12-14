# Public_KETI-IBMC 
<br/>


## Table of Contents
1. [Introduction of IBMC](#introduction-of-ibmc)  
2. [Technologies Used](#technologies-used)  
3. [Requirements](#requirements)  
	3.1. [Buildroot 환경 구성](#1-buildroot-환경-구성)  
	3.2. [Buildroot menuconfig](#2-buildroot-menuconfig)    
	3.3. [이미지 빌드](#3-이미지-빌드)  
	3.4. [BMC에 이미지 쓰기](#4-bmc에-이미지-쓰기)  
4. [Usage](#usage)  
	4.1. [빌드](#1-빌드)  
	4.2. [BMC 상에서 KETI-IPMI/KETI-Ibmc 실행](#2-bmc-상에서-keti-ipmiketi-ibmc-실행)    
	4.3. [KETI-REST 실행](#3-keti-rest-실행)  
	
	



## Introduction of IBMC

<br/><br/>


![no image](https://lh3.googleusercontent.com/fife/AAbDypAzcfA_yQllZ6o6QoXBrAu_H9pRjVFwmEckUWSiYSW-aR84i22IsqJkjY9zeIscIujvWrFrU9qWFhgCPALNg54mlvTmBUfZJWkvkmokyc1eyc9Q-_bzBXskk4zo_LUtEjQphrsK5Ncxy2TxnRLeiSA2seVCfGAoLyMwNQU8q1atYCiUA70Jvm88Xp5MMsHZ__gESMbZkIGgWAnDyWv0bkS7X-uSjmx64roShq0t3d_yLzR_ZPZrxdIQc7IoUdP35uxWkkiEeGFLb2b2kAzqVh8r16PkFK9r7kTD_4Kym8hmeUTMNGoMypVRY102JzTHd7wd_lFAqstUvG-DwGeTTFLCqTxrSuDSrZLicMnl-r5ka8Nsurbekn_zKdUxopsM9eTXK-HBMl9HAVOHTzJ048Du9PaOWyUAgCrAJ5nOD5_q29oP8zcwiWYhulnd0_YtI8xVm_tfxHbNxwbR0eFyU6Rx1filMbGgKRUAQkEDyucgn_73oVSwACK4MNvbW1P8Qz8SCINdnW-3TNuBs_IxHVlN3JS2QeHWifbPcmLSlBN7UZVt6aloUaIcTL_o-IkwiyiYr6zdqnyhevT-tYkDcqorgYBMJyw8FAZlAT1VeIAOfM37Xj5RPHy_ZA5nVg8o2TurTgO8yIM-9aZCQaylz_Fs8kWaBxp6CJlbtf-pZAEeRQttVCW6_5pXZiIdeDBRZEz9S-ZMeh21k0MbdNhj_G-tU5cPxM_gY2n8fRp2CHJgEG6k7ulr6n9OGGn4iKsQ1I9-G6YVUrzL4DDjqhe8PxFxyZQc9g2Wei6jVhHpWv3L-vSOzoWbtXmcfWETPSgGNnfszSVyEMmCJQX_Bu_837pQKmaMDxmuqq33aGfSI6Xw6KzHucW2yHiVsaHk3FzUwiLwdCJBph004oCtfyqbQhEcvQuqdlT3otixwKSWHBW91HyxllYfPq-VOOYnBk8Zohso0EiYWAM7T8YsUZ6qE6zrJKVwjslcLH4PRuvdm0-X8y_vVYurqjqfi5sJZipu1AfUpMKcO32Kps6lSqxtLTGsihmFCGxCFxeUagRl7jnkenujYH30UTCVoQukEJtamP8wr8YMxk6azb-OkllzEMtBISsafBZchn5AhWTJ6NAi2MrkJE5KxpIsbnLWeoh2i8jK5U-E_t1ZysSR8bAvfyHM1MG6HpR7rzw65Um9YzyxAynahz8egkNHJE4b-vykgBI3H37N370tmHLqpMSBS983ZkWtwtyUfitvUpFFDjAzBhLlhX9gqQw0ng8_dV8oF027bXMHHd61nV563EC3MvGz2OaheUV06rrF9vbl62BIz51E2kKKcLmff4KZ1m1Tgk9sBTyGKZmjecnINzzE3sbtfpJ-nTlv00W7Y9oQtnIoFA5iOIUmBgwWO43k2RxWKB1jL93DPkttWxIq3i70eyOfwDfK9iVCFpYkV44zQvBUjZ2v_1CjEYg8A_38pAsJuOgIyLpBQJv1t3f4xrXuwA=w1278-h1312)

<br/><br/>
>**서버의 메인보드에 내장된 컨트롤러로 시스템 관리 S/W와 H/W간의 인터페이스를 통해 On Device AI을 활용한 지능형 소비전력 + 장애 관리 펌웨어 SW 기술**   

<br/><br/>



## Technologies Used
### 1. 지능형 메인보드 제어용 BMC 소프트웨어 구조 설계 및 학습모델 런타임 엔진 프로토타입
 - 로컬/원격 기반 On Device AI 기능 탑재 지능형 메인보드 제어 BMC 메시지 송수신 프로토콜  
 - KETI-IBMC(BMC Control Module) 중심의 지능형 BMC Framework 구성  
 - 서버 메인보드 제어 및 운용을 위한 BMC SW Framework 통합 빌드 구조 설계, 환경 구현  
 - Application Layer, Framework Layer, Library Layer, Fast Booting Layer로 총 4단계의 Layer로 구성된 지능형 BMC 통합 펌웨어  
 - Buildroot 기반 BMC_SDK 통합 빌드 환경 및 해당 환경에서 AST2600 Toolchain을 활용한 크로스 컴파일 환경 구축  
 - AST2600 환경 Tensorflow Lite Micro의 On Device AI 기반 추론 기능 제공 모듈  

### 2. DMTF Redfish 기반 원격 모니터링 및 제어 기술
 - Redfish 기반 서버 시스템 제어 관리 구조 규격(Schema)  
 	- Redfish 기반 컴퓨팅 모듈 제어⸱관리를 위한 Interface  
 	- 지능형 BMC 컴퓨팅 모듈 제어를 위한 Redfish Schema 
 - Redfish 기반 모듈(Enclosure, Power, FAN) 구성 및 제어⸱관리 프로토타입 모듈  
 - System DBus 기반 지능형 BMC System 펌웨어 KETI-IBMC 설계 및 적용  
 	- Redfish Schema 요청 처리를 위한 Redfish API 연동 구조 설계 및 API 정의  
 - Redfish 기반 서버 시스템 제어⸱관리를 위한 GUI Interface


### 3. 컴퓨팅 서버 에너지(공급전원) 관리의 효율화 및 장애 진단 기술
 - 지능형 BMC 기반 에너지 임계치 관리  
 	- On Device AI 환경 컴퓨팅 모듈 동작을 위한 Hibernation Engine(에너지 관리 효율화) 및 Feedback Engine(장애 진단 기술) 모듈 연동  
 - 예측 데이터 기반 전원 관리 모드 및 스마트 쿨링 알고리즘   
  	- 설정된 CPU 온도를 기준으로 실시간 모니터링을 통헤 현재 CPU 온도에 따라 팬의 속력을 조절하여 컴퓨팅 모듈의 전원을 관리하는 BFC(Basic-Fan Speed-Control) 알고리즘
	- 컴퓨팅 모듈 소비전력 감소를 위한 LFC(Look-Ahead Fan Speed Control) 알고리즘   
  	- On Device AI 구현 모듈을 통해 만들어진 팬 속도 추론 알고리즘을 사용한 팬 속도 제어 
 - 센서 모니터링 정보 기반 컴퓨팅 모듈 이상 감지 및 고장 감내 관리 모듈 
 - 서버 장애 진단을 위한 FDM(Fault Diagnosis and Management)   
 	- FOFL(Fault Outbreak Feedback Level) 설정을 통한 실시간 오류 단계별 처리 및 장애 진단 
 - 서버 장애에 따른 MCE(Machine Check Exception) 상황 통합 관리   
  	- FOFL 단계에 따른 서버 장애 및 오류 상황 통합관리 기술 및 피드백  
  	- FOFL Range 제어를 기반으로 컴퓨팅 모듈 센서별 오류 감지 및 고장 관리 커스터마이징 기능 

### 4. 서버 시스템 모니터링 데이터 기반 실시간 분석 기술
 - 스트림 데이터 분석을 위한 데이터 추출·변환·연계(ETL, Extract-Transform-Load) 기술  
 - 실시간 탐지 정책 기반 오류 탐지 및 탐지 데이터 연동 기술 모델  
 - 서버 시스템 실시간 모니터링 및 On Device AI를 통한 서버 시스템의 부품 장애 진단  


<br/><br/>



## Requirements  


### 1. Buildroot 환경 구성
1. prepare_buildTool.sh 를 실행
 - cvs, libncurses-dev, libc6:i386, libncurses5:i386, libstdc++6:i386,zlib1g:i386, u-boot-tools, git 패키지 설치
```bash
$ ./prepare_buildTool.sh
```
  
  
### 2. Buildroot menuconfig  

 - 함께 제공되는 config 파일과 toolchain을 직접 다운로드 후 설치 필요
 - buildroot 파일 압축을 해제한 디렉토리에서 make menuconfig를 입력하면 Buildroot에 대한 전반적인 설정이 가능하다. 가장 먼저 아래와 같이 설정한다.

 
 1. Target Option 설정  


|    Target Option  | AST2500 |   AST2600                                         |                                           
| ------ | -------- | ------------------------------------------------ |  
|  Target Architecture  | ARM ( little endian) |   ARM ( little endian )   |  
|  Target Binary Format |  ELF                 |    ELF                   |  
|  Target Architecture Variant |  arm1176jzf-s  |    Cortex-A7             |  
|  Target ABI            |  EABI                |     EABIhf               |  
|  Floating point strategy | soft float          | VFPv4-D16              |  
|  ARM Instruction set   |   ARM                |  ARM                   |  


 
 2. Toolchain 설정  
 > Toolchain type : External toolchain  
 > Toolchain : External Toolchain -> Pre-installed toolchain  
 
 > Toolchain origin    
 	- downloaded and installed : Toolchain을 다운받을 주소 입력  
 	- Pre-installed toolchain : Toolchain이 설치된 절대경로 입력  
 
 > Toolchain path를 절대경로로 변경  
 	- Toolchain 경로  
 		- AST2500 : /home/keti/Workspace/buildroot/source/armv6-aspeed-linux-gnueabi  
 		- AST2600 : /home/keti/BMC_SDK/source/arm-aspeed-linux-gnueabihf  
 
 > Toolchain prefix 입력  
 	- AST2500 : armv6-aspeed-linux-gnueabi  
 	- AST2600 : arm-linux  
 
 
 > External toolchain gcc version  
```bash
External toolchain의 gcc 버전 확인    
$ ./armv6-aspeed-linux-gnueabi-gcc –v  

확인 후 해당 버전으로 설정
```

  
> External toolchain C library를 glibc/eglibc로 변경
> 기타 Toolchain 설정  

<br/><br/>






### 3. 이미지 빌드
<br/>

- Buildroot로 이미지 빌드  
- 빌드한 이미지는 ./output/images/all.bin 파일로 생성됨  


#### AST2500  
```bash
$ ./build_option.sh -i -m -s -c -n
```
**build_option.sh 옵션**  

-i : Static / DHCP 설정 (1로 설정 시 IP : 10.0.6.111, 2로 설정 시 IP : 10.0.6.112, 3 : DHCP)  
-m : MTD 적용 옵션 (0 : ramdisk 부팅 / 1 : cramfs / 2 : NFS 부팅)  
\* NFS 적용 시 s, n, c 옵션을 적용해야 함.  
-s : NFS Server IP Address  
-c : NFS Client IP Address  
-n : NFS Server Directory  
<br/>
기본적으로 Static IP 또는 NFS의 Gateway IP Address는 10.0.0.1, Netmask는 255.255.248.0으로 설정되어 있음. 따라서 환경 구축 시 참고하여 구축 해야함.  

ex)  
```bash
$ ./build_option.sh –i 3 –m 0
```
<br/>

#### AST2600  
```bash
$ ./build.sh -i -c -g -n
```  
**build.sh 옵션**  

-i : interface 적용 옵션 0 : DHCP / 1 : Static  
-c : BMC ip address  
-g : BMC gateway ip address  
-n : BMC netmask address  
<br/>
ex)  
```bash
$ ./build.sh -i 1 -c 10.0.6.104 -g 10.0.0.1 -n 255.255.240.0
```



### 4. BMC에 이미지 쓰기
#### AST2500(2600)-EVB
1. 빌드한 이미지 파일을 FTP로 다운받아 Windows 10 디렉토리로 옮김
2. AST2500 Evaluation Board의 좌측에 점퍼 케이블 중 오른쪽 핀을 빼서 GND에 연결하여 BMC Booting을 Disable 
3. 좌측 상단에 GND 핀에 점퍼 케이블을 연결
4. SF100-ISP Programmmer를 BMC ROM에 연결
5. AST2500 Evaluation Board 전원 켜기
6. Dediprog Engineering 소프트웨어를 실행시킨 뒤 Memory Type을 설정
7. Load file 버튼을 클릭하여 다운받은 all.bin 파일을 불러옴
8. Erase 버튼을 클릭하여 롬을 초기화한 뒤 Prog 버튼을 클릭하여 새 이미지를 기록
9. BMC Booting 점퍼 와이어를 다시 연결하고 SF100-ISP Programmer를 제거
10. 전원 인가

#### 32MB/64MB ROM
1. 펌웨어를 기록할 ROM을 칩 좌측 상단의 점(1번 핀)을 기준으로 장착
2. SF100 ISP Programmer에 롬을 장착한 뒤 PC에 연결
3. Dediprog Engineering을 실행한 뒤 장착한 ROM의 모델명을 선택
4. 좌측 상단의 File 버튼을 클릭하여 기록할 펌웨어 이미지 파일을 선택
5. Batch 버튼을 클릭하여 이미지를 기록
6. 기록이 완료되면 서버보드의 BMC ROM 장착 위치에 방향이 맞게 장착



## Usage

### 1. 빌드
#### AST2500
```bash
$ cd /home/keti/Workspace/buildroot/source/ast_app
$ ./sk_make.sh
```
ast_app/KETI-IPMI 경로에 KETI-IPMI 파일 생성됨

#### AST2600
```bash
$ cd /home/keti/BMC_SDK/source/AST2600_BMC
$ ./bmc_build.sh
```
AST2600_BMC/output/bin 경로에 KETI-Ibmc 파일 생성됨  


<br/>  


### 2. BMC 상에서 KETI-IPMI/KETI-Ibmc 실행


#### AST2500

```bash
$ KETI-IPMI
```

#### AST2600
```bash
$ KETI-Ibmc
```

<br/>  



### 3. KETI-REST 실행
#### AST2500

```bash
# 8000번 포트 사용
$ restful_server
```  

#### AST2600

```bash
$ ./KETI-REST
```
<br/>  






