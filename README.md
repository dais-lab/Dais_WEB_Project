#  Side Project -> Django를 활용한 웹사이트 제작하기
 
  * 추후 개발했던 방법에 대해서 기록을 남기고자 합니다.

 <br>

## 🚗 How to run
*우분투 -> 도커편

1. 도커 허브(https://hub.docker.com/)에서 아나콘다 최신 이미지를 다운받아주세요.
```
  docker pull continuumio/anaconda3:latest
```
2. 로컬 환경에서 /home/pratice/ 폴더를 만들고, Dais_WEB_Project repository를 clone해주세요.
```
  mkdir /home/pratice/
  cd /home/pratice/
  git clone https://github.com/dais-lab/Dais_WEB_Project.git
```

3. 시크릿키를 발급 받아서 깃허브 홈디렉토리에 secrets.json 파일을 생성 후 기입해주세요.
```
  cd Dais_WEB_Project/
  https://www.miniwebtool.com/django-secret-key-generator/
  vi secrets.json
  {
    "SECRET_KEY": "..."
  }
```
4. 격리된 컨테이너 공간을 생성합니다.
```
docker run --name Lab -v /home/pratice/:/working_docker_folder -p 8000:8000 continuumio/anaconda3:latest

## 도커 환경에 진입했다면, 파이썬 3.6.4 버전으로 가상환경 생성.
conda create -n lab python=3.6.4
conda activate lab

## 도커 환경에 진입하지 못했다면
docker start Lab
docker exec -it Lab bash
## 파이썬 3.6.4 버전으로 가상환경 생성.
conda create -n lab python=3.6.4
conda activate lab
```
5. 생성된 가상환경 내에서 필요한 패키지 설치해주세요.
```
  cd /working_docker_folder/Dais_WEB_Project/
  # mysqlclient를 설치하기 위해 아래 코드를 진행.
  apt-get update
  apt-get install python3.9-dev default-libmysqlclient-dev build-essential
  pip install mysqlclient
  pip install -r requirements.txt
```

6. 프로젝트 실행에 필요한 테이블을 생성해주세요.
```
python manage.py migrate
```

7. 웹 어플리케이션(WAS)을 실행시켜주세요.
```
python manage.py runserver 0.0.0.0:8000
```

8. 웹 사이트에 아래 링크를 입력해주세요.
```
http://127.0.0.1:8000/app/main or http://외부IP:8000/app/main or http://도메인:8000/app/main 
```

<br>

## ⚙ Environment

Frontend

```
- bootstrap4 : 0.1.0
```

Backend

```
- django version : 3.2.11
```

Database

```
- MySql
```

<br>

## ⚡ tech-stack

### front-end

- bootstrap
- css

### backend

- django
- Mysql

## tools
- github
- erd cloud
- adove xd

<br>

## 📅 Development period

2022.01.30 ~ 2022.02.03(5-Days)