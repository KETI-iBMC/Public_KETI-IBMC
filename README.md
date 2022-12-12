# Public_KETI-IBMC 
<br/>


## Table of Contents
1. [Introduction of IBMC](#introduction-of-ibmc)
2. [Requirements](#requirements)  
	2.1. [Buildroot 환경 구성](#1-buildroot-환경-구성)  
		2.1.1. [AST2500](#1-ast2500)  
		2.1.2. [AST2600](#2-ast2600)  
	2.2. [Buildroot menuconfig](#2-buildroot-menuconfig)  
	2.3. [KETI-IPMI 빌드](#3-keti-ipmi-빌드)  
	2.4. [이미지 빌드](#4-이미지-빌드)  
	2.5. [BMC에 이미지 쓰기](#5-bmc에-이미지-쓰기)  
3. [Usage](#usage)  
	3.1. [KETI-IPMI 실행](#1-keti-ipmi-실행)    
	3.2. [KETI-REST 실행](#2-keti-rest-실행)  
	3.3. [KETI-REST 지원 API 리스트 및 URL](#3-keti-rest-지원-api-리스트-및-url)
	



## Introduction of IBMC

<br/><br/>


![no image](https://lh3.googleusercontent.com/fife/AAbDypAzcfA_yQllZ6o6QoXBrAu_H9pRjVFwmEckUWSiYSW-aR84i22IsqJkjY9zeIscIujvWrFrU9qWFhgCPALNg54mlvTmBUfZJWkvkmokyc1eyc9Q-_bzBXskk4zo_LUtEjQphrsK5Ncxy2TxnRLeiSA2seVCfGAoLyMwNQU8q1atYCiUA70Jvm88Xp5MMsHZ__gESMbZkIGgWAnDyWv0bkS7X-uSjmx64roShq0t3d_yLzR_ZPZrxdIQc7IoUdP35uxWkkiEeGFLb2b2kAzqVh8r16PkFK9r7kTD_4Kym8hmeUTMNGoMypVRY102JzTHd7wd_lFAqstUvG-DwGeTTFLCqTxrSuDSrZLicMnl-r5ka8Nsurbekn_zKdUxopsM9eTXK-HBMl9HAVOHTzJ048Du9PaOWyUAgCrAJ5nOD5_q29oP8zcwiWYhulnd0_YtI8xVm_tfxHbNxwbR0eFyU6Rx1filMbGgKRUAQkEDyucgn_73oVSwACK4MNvbW1P8Qz8SCINdnW-3TNuBs_IxHVlN3JS2QeHWifbPcmLSlBN7UZVt6aloUaIcTL_o-IkwiyiYr6zdqnyhevT-tYkDcqorgYBMJyw8FAZlAT1VeIAOfM37Xj5RPHy_ZA5nVg8o2TurTgO8yIM-9aZCQaylz_Fs8kWaBxp6CJlbtf-pZAEeRQttVCW6_5pXZiIdeDBRZEz9S-ZMeh21k0MbdNhj_G-tU5cPxM_gY2n8fRp2CHJgEG6k7ulr6n9OGGn4iKsQ1I9-G6YVUrzL4DDjqhe8PxFxyZQc9g2Wei6jVhHpWv3L-vSOzoWbtXmcfWETPSgGNnfszSVyEMmCJQX_Bu_837pQKmaMDxmuqq33aGfSI6Xw6KzHucW2yHiVsaHk3FzUwiLwdCJBph004oCtfyqbQhEcvQuqdlT3otixwKSWHBW91HyxllYfPq-VOOYnBk8Zohso0EiYWAM7T8YsUZ6qE6zrJKVwjslcLH4PRuvdm0-X8y_vVYurqjqfi5sJZipu1AfUpMKcO32Kps6lSqxtLTGsihmFCGxCFxeUagRl7jnkenujYH30UTCVoQukEJtamP8wr8YMxk6azb-OkllzEMtBISsafBZchn5AhWTJ6NAi2MrkJE5KxpIsbnLWeoh2i8jK5U-E_t1ZysSR8bAvfyHM1MG6HpR7rzw65Um9YzyxAynahz8egkNHJE4b-vykgBI3H37N370tmHLqpMSBS983ZkWtwtyUfitvUpFFDjAzBhLlhX9gqQw0ng8_dV8oF027bXMHHd61nV563EC3MvGz2OaheUV06rrF9vbl62BIz51E2kKKcLmff4KZ1m1Tgk9sBTyGKZmjecnINzzE3sbtfpJ-nTlv00W7Y9oQtnIoFA5iOIUmBgwWO43k2RxWKB1jL93DPkttWxIq3i70eyOfwDfK9iVCFpYkV44zQvBUjZ2v_1CjEYg8A_38pAsJuOgIyLpBQJv1t3f4xrXuwA=w1278-h1312)

<br/><br/>
>**서버의 메인보드에 내장된 컨트롤러로 시스템 관리 S/W와 H/W간의 인터페이스를 통해 On Device AI을 활용한 지능형 소비전력 + 장애 관리 펌웨어 SW 기술**   

<br/><br/>

## Requirements  

### 1. Buildroot 환경 구성

#### 1. AST2500  

1. 파일 내려받기 ( 현재 위치 : /home/keti/Workspace )  
<https://buildroot.org/downloads/buildroot-2015.11.tar.gz>  


2. 내려받은 압축 파일 해제  
```bash
$ tar -xvzf buildroot-2015.11.tar.gz
```
	
3. 해당 디렉토리 진입  
```bash
$ cd buildroot-2015.11.tar.gz
```  
	
4. KETI-IPMI.tar 압축을 풀어 ./source/ast_app 디렉토리에 복사  (KETI-IPMI.tar는 소스코드와 함께 제공됨)
```bash
$ tar -xvzf KETI-IPMI.tar  
$ cp -r KETI-IPMB ./source/ast_app  
```  
  
5. prepare_buildTool.sh 를 실행
```bash
$ ./prepare_buildTool.sh
```  

#### 2. AST2600  
- **Buildroot 2020.08** 버전 설치
```bash
/home/keti/BMC_SDK
$ ./prepare_buildTool.sh
```
<br/>  

> Buildroot 공식 홈페이지에서 권장하는 패키지와 옵션 패키지  
- Mandatory : <https://buildroot.org/downloads/manual/manual.html#requirement-mandatory>
- Optional : <https://buildroot.org/downloads/manual/manual.html#requirement-optional>  
<br/><br/>
  
  
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
 		- AST2500 : /home/keti/Workspace/buildroot-2015.11/source/armv6-aspeed-linux-gnueabi  
 		- AST2600 : $(ROOT_DIR)/source/arm-aspeed-linux-gnueabihf  
 
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


### 3. KETI-IPMI 빌드

#### AST2500
```bash
$ make toolchain
$ make
$ cd /home/keti/Workspace/buildroot-2015.11/source/ast_app
$ ./sk_make.sh
```


#### AST2600
```bash
$ cd /home/keti/BMC_SDK/source/AST2600_BMC
$ cmake CMakeLists.txt
$ make
```

### 4. 이미지 빌드
<br/>

- Buildroot로 이미지 빌드  
- 빌드한 이미지는 ./output/images/all.bin 파일로 생성됨  


#### AST2500  
```bash
$ ./build_option.sh
```

#### AST2600  
```bash
$ ./build_option.sh
```

-i : Static / DHCP 설정 (1로 설정 시 IP : 10.0.6.111, 2로 설정 시 IP : 10.0.6.112, 3 : DHCP)  
-m : MTD 적용 옵션 (0 : ramdisk 부팅 / 1 : cramfs / 2 : NFS 부팅)  
* NFS 적용 시 s, n, c 옵션을 적용해야 함.  

-s : NFS Server IP Address  
-c : NFS Client IP Address  
-n : NFS Server Directory  
<br/>
기본적으로 Static IP 또는 NFS의 Gateway IP Address는 10.0.0.1, Netmask는 255.255.248.0으로 설정되어 있음. 따라서 환경 구축 시 참고하여 구축 해야함.  
<br/>
Ramdisk 예시 : ./build_option.sh –i 3 –m 0  
CRAMFS 예시 : ./build_option.sh –i 3 –m 1  
NFS 예시 : ./build_option.sh –i 3 –m 2 –s 10.0.6.123 –c 10.0.6.124 –n /nfs/ast_ktnf/  



### 5. BMC에 이미지 쓰기
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

### 1. KETI-IPMI 실행
```bash
$ KETI-IPMI
```


### 2. KETI-REST 실행
```bash
# 8000번 포트 사용
$ restful_server
```  

### 3. KETI-REST 지원 API 리스트 및 URL
- System Information  

|   ID   |    URL   |   Method   |                   상세기능                 |
| ------ | -------- | ---------- | ------------------------------------------ |
|  ST01  | /sysinfo |    GET     |        IPMI 및 BMC 정보 제공                |


<br/>

- FRU Information  

|   ID   |    URL   |   Method   |               상세기능        |     
| ------ | -------- | -----------|------------------------------- |
|  FU01  |   /fru   |     GET    |    BMC FRU 정보 제공            |
|  FU02  |   /fru   |     PUT    |    BMC FRU 정보 수정             |

<br/>

- Server Health  

|   ID   |    URL   |   Method   |                       상세기능                       |     
| ------ | -------- | -----------   |---------------------------------------------------- |  
|  SH01  |   /sensor   |     GET    |    센서 상태 정보 제공                            |
|  SH02  |   /sensor   |     PUT    |    센서 Threshold 값 수정                         |
|  SH03  |   /event    |     GET    |    BIOS, Sensor, System Event Log 정보 제공       |

- Configuration

|   ID      |   URL    |   Method        |                   상세기능                                              |  
|---------- |----------|-----------------|-------------------------------------------------------------------------|  
|  CF01      |   /ddns    |     GET      |         Dynamic DNS 설정 정보 제공                                    |  
|  CF02      |   /ddns     |    POST     |        Dynamic DNS 설정 정보 수정                                   |  
|  CF03      |    /network    |    GET    |        BMC 네트워크 정보 제공                                     |  
|  CF04      |    /network    |    POST     |       BMC 네트워크 정보 수정                                     |  
|  CF05      |   /ntp     |   GET      |            NTP(Network Time Protocol) 정보 제공                       |  
|  CF06      |   /ntp     |   POST      |           NTP 설정 정보 수정 (자동 / 수동)                           |  
|  CF07      |   /smtp     |   GET      |           SMTP(Simple Message Transfer Protocol) 정보 제공                    |  
|  CF08      |   /smtp     |   POST      |          SMTP 설정 정보 수정                     |  
|  CF09      |   /ssl     |   POST      |          SSL 인증서 생성                     |  
|  CF10      |   /ssl     |   GET      |          SSL 인증서 정보 제공                    |  
|  CF11      |   /activedir     |   GET      |          Active Directory 그룹 정보 제공                 |  
|  CF12      |   /activedir     |   POST      |          Active Directory 그룹 추가                 |  
|  CF13      |   /ldap     |   GET      |          LDAP 정보 제공                 |  
|  CF14      |   /ldap     |   PUT      |          LDAP 설정 정보 수정                 |   
|  CF15      |   /radius     |   GET      |         RADIUS 정보 제공                 |  
|  CF16      |   /radius     |   POST      |         RADIUS 설정 정보 수정               |  
|  CF17      |   /user    |   GET      |         BMC User 리스트 제공                |  
|  CF18      |   /user    |   POST      |         BMC User 정보 추가                |  
|  CF19      |   /user    |   DELETE      |         BMC User 삭제                |  
|  CF20      |   /activedir     |   DELETE      |          Active Directory 설정 정보 삭제                 |  

- Main Page  

|   ID   |    URL   |   Method   |                       상세기능                         |  
|---------- |----------|-------------|---------------------------------------------------|  
|   MP00  |   /main?INDEX=0    |   GET   |                   메인 페이지 모든 정보 제공                           |  
|   MP01  |   /main?INDEX=1    |   GET   |                   System Event Log 정보 제공                           |  
|   MP02  |   /main?INDEX=2    |   GET   |                   Memory Controller 온도 정보 제공                           |  
|   MP03  |   /main?INDEX=3    |   GET   |                   Ethernet Controller 온도 정보 제공                           |  
|   MP04  |   /main?INDEX=4    |   GET   |                  System Board 온도 정보 제공                            |  
|   MP05  |   /main?INDEX=5    |   GET   |                  Power Module 전력량과 전류량 정보 제공                            |  
|   MP06  |   /main?INDEX=6    |   GET   |                 서버보드 Fan, CPU Fan RPM 정보 제공                            |  
|   MP07  |   /main?INDEX=7    |   GET   |                 BMC 네트워크 설정 및 펌웨어 버전정보 제공                             |  
|   MP08  |   /main?INDEX=8    |   GET   |                센서 및 하드웨어 설치 유무 정보 제공                              |  

- Remote Control

|   ID   |    URL   |   Method   |                       상세기능                       |  
|---------- |----------|-------------|---------------------------------------------------|  
|   RC01   |    /power   |   GET   |                       Host 서버 전원 상태 정보 제공                      | 
|   RC02   |    /power   |   PUT   |                       Host 서버 전원 상태 제어                      |  

- Maintenance

|   ID   |    URL   |   Method   |                       상세기능                       |  
|---------- |----------|-------------|---------------------------------------------------|  
|   BR01   |    /bmcReset   |   POST   |                      BMC 공장 초기화 기능 제공                       |  
|   BR02   |    /wamReset  |   POST   |                      BMC 시스템 재부팅                       |  

- Settings

|   ID   |    URL   |   Method   |                       상세기능                       |  
|---------- |----------|-------------|---------------------------------------------------|  
|   SS01   |    /setting   |   GET   |                       BMC Setting 정보 제공                    |  
|   SS02   |    /setting   |   PUT   |                       BMC Setting 정보 수정                    |  




