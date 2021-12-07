# 🏭Smart Factory

## 주제

Cisco Packet Tracer를 이용하여 Smart Factory의 IoT 네트워크 환경을 구축한다. IP 주소는 203.230.7.0의 주소 안에서 Subnetting, VLSM 하여 각각에 알맞게 주소를 부여한다.

## 구성

![IoT전체](https://user-images.githubusercontent.com/64248143/145066669-f4745c6e-8298-4a1e-abe8-5f76afc49de2.JPG)

Smart Factory는 공장, 창고, 발전소로 3개의 cluster로 구성되었다. 공장을 중심으로 창고와 발전소가 연결되어있다. 3개의 cluster의 각 라우터는 시리얼 케이블로 서로 연결되어있으며, Router rip ver2가 설정되어있다.

- 발전소
    
    ![IoT발전소](https://user-images.githubusercontent.com/64248143/145066709-c6f19bab-c772-48c6-9b05-11675fe6197b.JPG)
    
    - 풍력 발전과 태양광 발전으로 이루어짐
    - wind turbine과 power monitor에 연결된 solar pannel이 각각의 battery에 연결됨
- 창고
    
    ![IoT창고](https://user-images.githubusercontent.com/64248143/145066759-e8ccd777-72f7-4c6c-b5dd-6793bdbd9618.JPG)
    
    - 서버와 PC 2개, Wireless Router 1개, Home Gateway 1개가 스위치를 통해 유선으로 라우터에 연결됨
    - Wireless Router 구간과 Home Gateway의 구간을 VLAN으로 나눔
    - Home Gateway에는 스마트 도어, 화재 감지기, 스마트 실링팬 등 다양한 IoT 디바이스들이 연결됨
        - ex) MCU 보드에 fire monitor와 sprinkler를 연결. fire monitor에서 불을 감지하면 sprinkler가 작동할 수 있도록 MCU 보드에 파이썬으로 코딩.
    - 서버는 AAA 서비스와 IoT 서비스를 지원하며 DNS server의 역할을 함
    - PC에서 DNS 서버의 주소에 접속하면 연결된 IoT 디바이스 제어 가능
    - 무선 네트워크 구간은 보안을 위해 SSID와 AAA를 사용해 허용된 사용자만 연결
- 공장
    
    ![IoT공장](https://user-images.githubusercontent.com/64248143/145066795-80dd6bd0-f501-4934-b731-c63c20eca8b8.JPG)
    
    - 서버와 PC, Home Gateway, Wireless Router, IoT 디바이스가 유선으로 스위치를 통해 라우터에 연결됨
    - 창고와 유사하게 Wireless Router 구간과 Home Gateway의 구간을 VLAN으로 나눔
    - 유선 연결된 3개의 IoT 디바이스를 제외한 나머지 IoT 디바이스들은 창고와 유사하게 무선으로 Home Gateway에 연결됨

## 개발환경

Cisco Packet Tracer 7.3.0
