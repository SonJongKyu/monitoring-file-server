**2024.09 (1人 개인 프로젝트)**

## **📌 Summary**

**서버 자원 상태를 실시간으로 모니터링하고, 장애 발생 시 Slack 알림을 전송하는 모니터링 시스템 구축 프로젝트**
- Prometheus와 Grafana를 사용해 CPU, 메모리, 네트워크 등의 상태를 시각화하고, Slack Webhook을 통해 실시간 알림 제공  
> 주요 기능: 서버 상태 수집, Grafana 대시보드 시각화, 임계치 초과 시 Slack 알림 전송

## **🤔 Background**

서버 운영 시 장애를 조기에 감지하지 못하면 서비스 품질 저하나 중단으로 이어질 수 있습니다.  
이를 방지하기 위해 운영 서버 상태를 실시간으로 모니터링하고, 임계치 초과 시 즉각 알림을 받을 수 있는 환경을 구축하고자 했습니다.  

## **🔍 Meaning**

이번 프로젝트를 통해 Prometheus와 Grafana의 연동 방식, 그리고 Slack Webhook을 통한 알림 자동화를 처음 경험했습니다.  
단순한 모니터링을 넘어, 실제 운영 환경에서 바로 활용할 수 있는 실시간 알림 시스템을 직접 구성했다는 점에서 의미가 컸습니다.  
또한, 팀원들과 서버 지표를 공유하고 분석하는 문화를 만들 수 있는 기반이 되었습니다.

## **🔨 Technology Stack(s)**

- Prometheus
- Grafana
- Slack Webhook
- Linux (Ubuntu)
- Shell Script

## **⚙️ Setup & Usage**

**1. Prometheus 설치**
```jsx
wget https://github.com/prometheus/prometheus/releases/download/v2.48.0/prometheus-2.48.0.linux-amd64.tar.gz
tar xvf prometheus-*.tar.gz
cd prometheus-*
```

**2. Grafana 설치**
```jsx
sudo apt-get install -y apt-transport-https software-properties-common
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
sudo apt-get update && sudo apt-get install grafana
```

**3. Prometheus와 Grafana 실행**
```jsx
./prometheus --config.file=prometheus.yml
sudo systemctl start grafana-server
```

**4. Slack Webhook 설정**
- Slack > 앱 추가 > Incoming Webhook > 채널 선택 후 URL 복사
- Alertmanager 설정 파일(alertmanager.yml)에 Slack Webhook URL 추가

**5. Grafana 접속**
- 브라우저에서 http://<서버_IP>:3000 접속  
- 기본 계정: admin / admin
