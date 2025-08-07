# loss_rc_yolo11

시간바꾸기
sudo timedatectl set-timezone 'Asia/Seoul'라는 코드를 써서 서울의 시간으로 컴퓨터의 시간을 바꾸세요.

아두이노에서는 한글 쉽게 쓸 수 없다. 그래서 한글을 설치하는 방법 Ubuntu에서 한글 입력이 잘 안 될 경우 fcitx-hangul을 설치하고 입력기 시스템을 fcitx로 설정하면 안정적으로 한글 입력이 가능합니다.

Interface Config의 줄임말
리눅스에서 네트워크 인터페이스 상태를 확인하고 설정하는 명령어입니다.

df = Disk Free
리눅스에서 사용 가능한 디스크 공간(용량)을 파일 시스템 단위로 보여주는 명령어입니다.

get clone 
Git에서 가장 많이 쓰이는 명령어 중 하나로, 원격 저장소(remote repository)를 복제(clone) 해서 내 컴퓨터로 가져올 때 사용돼요.

ls: 리스트
지금다운로드에 어떤 것이 있는지 알려달라는 것

cd Downloads
git clone https://github.com/jetsonworld/jetson-fan-ctl.git

jetson@nano:~/Downloads$ ls
installPiOLED  jetson-fan-ctl: 결과

jetson@nano:~/Downloads$ cd jetson-fan-ctl

lsjetson@nano:~/Downloads/jetson-fan-ctl$ ls
00_MIT_License.txt  automagic-fan.service  fanctl.py  README.md
01_Images    config.json     install.sh  uninstall.sh

jetson@nano:~/Downloads/jetson-fan-ctl$ sudo sh install.sh
위 코드를 써서 라이브러리를 설치함

그리고 롤링팬이 시끄러울 수 있습니다. 그럴땐 아래코드를 사용해 속도를 128로 바꾸세요
sudo sh -c 'echo 128 >/sys/devices/pwm-fan/target_pwm’

jetson@nano:~$ cd
jetson@nano:~$ sudo apt install python3-pip

sudo apt install python3-pip는 **Python 3용 프로그램 설치 도구(pip)**를 설치하는 명령어예요.

jetson@nano:~$ sudo -H pip3 install –U jetson-stats
jetson@nano:~$ reboot
jetson@nano:~$ jtop

sudo -H pip3 install –U jetson-stats: 모니터링 실시간 확인

클팬을 돌리기 전에 jtop으로 온도 확인 하고 쿨링팬 돌리고 온도 확인 한다.

1.5 I2C 장치 연결 확인
우리는 pca9685에 납땜을 해 주었기 때문에 60이 찍혀야 정상이다.
jetson@nano:~$ i2cdetect -y -r 1

jtop은 NVIDIA Jetson 보드를 위한 실시간 시스템 모니터링 툴입니다.
간단히 말하면, Jetson에서 CPU, GPU, 메모리, 전력 사용량 등 시스템 상태를 한눈에 보여주는 
대시보드라고 생각하면 됩니다.

aarch64
 64비트 ARM 아키텍처를 의미하는 용어입니다. 조금 더 풀어서 설명하면 이렇습니다
  ARM 아키텍처
  ARM은 저전력, 모바일, 임베디드 장치용    CPU 아키텍처입니다.
  스마트폰, 태블릿, 싱글보드 컴퓨터(예: Raspberry Pi, NVIDIA Jetson)에서 많이 사용됩니다.
  ARM CPU에는 32비트(ARMv7)와 64비트(ARMv8 이상) 버전이 있습니다.

PCA9685는 I²C 통신을 사용하는 16채널 PWM(Pulse Width Modulation) 컨트롤러 칩입니다. 주로 
라즈베리파이, 아두이노, NVIDIA Jetson 같은 마이크로컨트롤러/싱글보드 컴퓨터에서 서보 모터, 
LED 밝기 조절, 모터 속도 제어 등에 사용됩니다.

GPIO란?
**GPIO (General Purpose Input/Output)**는 범용 입력/출력 핀을 뜻합니다.마이크로컨트롤러(라즈베리파이, 아두이노, Jetson 등)에서 센서, LED, 버튼, 모터 등 외부 장치와 
데이터를 주고받는 핀입니다.

우분투에서 sftp를 연결하는 방법은 아래 그림을 참고하세요. sftp로 연결하여 Jetson에 있는 
파일을 PC에서 쉽게 변경, 편집할 수 있습니다. Jetson Ubuntun에 있는 vi, nano등 툴이 
익숙하지 않으면 이 방법을 이용하는 것이 가능합니다. 즉 PC geditor로 
Jetson 파일을 수정할 수 있습니다.

ROS2를 설치할 수 있는 script를 download하여 설치합니다. Jetson에서 아래를 실행해주세요. 
PC에서 remote 작업을 하려면 PC에도 동일하게 설치해주세요.

jetson@nano:~/Downloads$ ls
installPiOLED  jetson-fan-ctl

jetson@nano:~/Downloads$ git clone -b galactic https://github.com/zeta0707/installROS2.git

jetson@nano:~/Downloads$ ls
installPiOLED  installROS2  jetson-fan-ctl

jetson@nano:~/Downloads$ cd installROS2/



느낀점
NVIDIA Jetson 보드와 ROS2 Galactic을 기반으로 자율주행 RC카를 구현하기 위한 매우 상세하고 체계적인 실무 매뉴얼로 느낌 단순한 설치와 빌드를 넘어, I2C 장치 제어, 실시간 모니터링(jtop), ROS2 워크스페이스 관리, USB 카메라 셋업, 토픽과 노드의 상호작용, 그리고 HSV 필터를 이용한 물체 추적과 YOLO 기반 객체 인식까지 다양한 기술 스택과 실전 팁들이 조화롭게 어우러져 있어. 특히 환경변수 설정, alias 함수 등록 같은 개발 효율성 증대 방법과, 실시간 디버깅 툴(rqt_graph, rqt_image_view) 활용법, 그리고 커스텀 데이터셋 학습 후 신호등 인식에 따른 주행 제어까지 ‘현장에서 바로 쓸 수 있는’ 완성도 높은 프로젝트 가이드임을 매우 잘 느낌 로봇 소프트웨어 개발에 익숙하지 않은 초보자도 따라 할 수 있게 단계별로 잘 풀어내면서도, 고급 주제까지 아우르는 점이 인상적이고, 실제 하드웨어 제어와 AI 인식이 융합된 통합 시스템 구축의 좋은 것 이라고 생각함, ai가 편하다는 걸 느끼고 복사붙여넣기는 엄청나게 유용하다는 걸 다시한번 세게 느끼게됨












