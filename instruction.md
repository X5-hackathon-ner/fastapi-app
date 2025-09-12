# NER Hackathon — Участнику: быстрый старт

Эта инструкция показывает, как развернуть простейший FastAPI-сервис с эндпоинтами /health и /api/predict под наш контракт на виртуальной машине. Участники могут использовать любую облачную платформу для размещения виртуальной машины, в данной инструкции используется Яндекс облако.

1. Авторизуйтесь на [сайте](https://yandex.cloud/ru)
2. Создайте пару SSH-ключей и виртуальную машину с публичным IP по [инструкции](https://yandex.cloud/ru/docs/compute/operations/vm-connect/ssh#linux-macos_1)
3. Подключитесь с локальной машины:

```bash
ssh <имя пользователя>@<публичный_IP>
```

4. Установите docker:
```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable docker
sudo systemctl start docker
```

Проверьте командой
```bash
docker --version
```
5. Установите Git:

```bash
sudo apt install git -y
```
6. Склонируйте репозиторий с базовой моделью:

```bash
git clone https://github.com/X5-hackathon-ner/fastapi-app.git
```
7. Соберите образ

```bash
cd fastapi-app
sudo docker build -t fastapi-app .
```
Запустите контейнер

```bash
sudo docker run -d -p 8000:8000 fastapi-app
```
Проверьте, что контейнер работает

```bash
sudo docker ps
```
После старта контейнера перейдите по адресу ```http://<публичный_IP>:8000/health```. В случае успешной работы сервиса эндпоинт вернёт ответ ```{"status": "ok"}```.

8. В телеграмм боте при регистрации команды/смене URL введите ```http://<публичный_IP>:8000```
9. Логи обработки входящих запросов можно увидеть, выполнив команду

```bash
sudo docker logs <container_id>
```

container_id можно найти в выводе команды

```bash
sudo docker ps
```
