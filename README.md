Это калька с оригинального проекта крутого чувака https://github.com/jciolek/docker-protractor-headless
Спасибо ему большое)

Использование:
Запускаем из деректории с проектом

docker run -it --privileged --rm --net=host -v /dev/shm:/dev/shm -v $(pwd):/protractor docker_image_with_protractor [protractor options]

В моем случае:

"docker run -it --privileged --rm --net=host -v /dev/shm:/dev/shm -v $(pwd):/protractor docker-protractor:2.0 config.js"

[protractor options] я указывал config файл. Также можно использовать все commandline options для проктрактора, например baseUrl, specs и т.д..

Как мы дошли до такой жизни? - Оригинальный имадж https://hub.docker.com/r/webnicer/protractor-headless/ у меня почему-то не завелся. Но имея ссылку на проект чувака на гитхабе я немного подправил конфиг файл(с учетом ошибок на которые ругался протрактор и пересобрал докер-имадж).
Если у вас тоже что-то пошло не так, то:
- клоним себе проект
- переходим в папку с склонированным проектом
- читаем как собирается и ранится имадж с под докера
- редактируем Dockerfile
- собираем свой имадж, я собирал так - "docker build -t your_image_name ." Докер сам поймет что нужно брать докер файл. Важно! Не провтыкать в конце команды точку, иначе нифига не соберется  и придется долго чехлить что же не так. Ждем сборки, при необходимости ходим уже в сам имадж и правим что нам надо(оригинальный у меня ругался и не пускал...)
- запускаем тесты(описано выше)
- Profit!
