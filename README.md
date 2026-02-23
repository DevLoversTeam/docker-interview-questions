<h1>
  Docker <img src="./assets/docker.svg" width="40" height="40" />
</h1>

<h2>Найпопулярніші запитання та відповіді на співбесіді з Docker</h2>

<details>
<summary>1. Що таке Docker?</summary>

#### Docker

**Docker** — це платформа для розробки, доставки й запуску застосунків у
контейнерах. Контейнер містить застосунок і його залежності, тому працює
однаково на різних середовищах.

Docker допомагає уникати проблеми "працює в мене локально, але не працює на
сервері", бо середовище стандартизоване.

**Коротко:**

- Docker запускає застосунки в контейнерах.
- Контейнери ізолюють процеси та залежності.
- Дає однакову поведінку локально, на CI і в production.

</details>

<details>
<summary>2. Які основні переваги використання Docker?</summary>

#### Docker

Основні переваги:

1. **Портативність**: один і той самий образ запускається всюди.
2. **Швидкий старт**: контейнер запускається за секунди.
3. **Ізоляція**: залежності одного сервісу не конфліктують з іншими.
4. **Простий деплой**: замість "налаштовувати сервер" — "запустити образ".
5. **Ефективність ресурсів**: контейнери легші за повноцінні ВМ.

**Коротко:**

- Швидше розробка і релізи.
- Менше конфліктів середовища.
- Краща утилізація інфраструктури.

</details>

<details>
<summary>3. Які проблеми вирішує Docker?</summary>

#### Docker

Docker вирішує типові інженерні проблеми:

- різниця між локальним, тестовим і production середовищем;
- складний онбординг нового розробника;
- ручне керування залежностями та версіями;
- нестабільні деплоя через дріфт конфігурацій;
- важке масштабування сервісів.

**Коротко:**

- Усуває environment drift.
- Стандартизує запуск застосунку.
- Спрощує CI/CD і масштабування.

</details>

<details>
<summary>4. Що таке контейнер у Docker?</summary>

#### Docker

**Контейнер** — це запущений екземпляр Docker-образу. Він має власний
файловий шар для запису, ізольований простір процесів, мережу та налаштування.

Контейнер еферемерний: його можна швидко створити, зупинити, видалити і
перезапустити.

**Коротко:**

- Контейнер = runtime-стан образу.
- Ізольований процес з власним оточенням.
- Швидко створюється й видаляється.

</details>

<details>
<summary>5. Чим контейнер відрізняється від віртуальної машини?</summary>

#### Docker

Ключова відмінність — рівень віртуалізації:

- **VM** віртуалізує апаратний рівень і має власну гостьову ОС.
- **Контейнер** віртуалізує рівень ОС і ділить kernel хоста.

Через це контейнери зазвичай:

- легші;
- швидше стартують;
- споживають менше ресурсів.

**Коротко:**

- VM важчі, але дають сильнішу ізоляцію ОС.
- Контейнери легші й швидші.
- Для мікросервісів частіше обирають контейнери.

</details>

<details>
<summary>6. Що таке Docker Image?</summary>

#### Docker

**Docker Image** — це незмінний шаблон (read-only), з якого створюються
контейнери. Образ містить файлову систему, застосунок, залежності та
метадані запуску.

Образи збирають через `Dockerfile` і зберігають у registry.

**Коротко:**

- Image — шаблон для створення контейнерів.
- Містить код, залежності та інструкції запуску.
- Сам по собі не виконується, доки не створено контейнер.

</details>

<details>
<summary>7. Чим відрізняються Image і Container?</summary>

#### Docker

- **Image** — статичний, незмінний артефакт.
- **Container** — запущений процес на основі image.

Один image може породжувати багато контейнерів із різним runtime-станом.

**Коротко:**

- Image = "шаблон".
- Container = "живий екземпляр".
- Багато контейнерів можуть використовувати один image.

</details>

<details>
<summary>8. Що таке Docker Engine?</summary>

#### Docker

**Docker Engine** — це базовий runtime Docker, який забезпечує збірку образів,
запуск контейнерів, керування мережами, томами та API взаємодію.

Це основний компонент, який встановлюється на сервер або локальну машину.

**Коротко:**

- Docker Engine — ядро платформи Docker.
- Керує життєвим циклом контейнерів.
- Надає API і CLI-інтеграцію.

</details>

<details>
<summary>9. З яких компонентів складається Docker Engine?</summary>

#### Docker

Docker Engine складається з:

1. **Docker Daemon (`dockerd`)** — серверна частина.
2. **Docker API** — інтерфейс взаємодії з daemon.
3. **Docker CLI (`docker`)** — клієнт для командного керування.

**Коротко:**

- `dockerd` виконує операції.
- API передає команди.
- CLI — зручна оболонка для користувача.

</details>

<details>
<summary>10. Що таке Docker Daemon?</summary>

#### Docker

**Docker Daemon** (`dockerd`) — це фоновий сервіс, який приймає Docker-команди
через API і виконує їх: збірка образів, запуск/зупинка контейнерів,
керування мережами та томами.

**Коротко:**

- `dockerd` — головний процес Docker на хості.
- Саме він реально створює та запускає контейнери.
- CLI звертається до нього через API.

</details>

<details>
<summary>11. Що таке Docker Client?</summary>

#### Docker

**Docker Client** — це CLI-інструмент `docker`, яким користувач вводить команди
на кшталт `docker run`, `docker ps`, `docker build`.

Client не запускає контейнери напряму — він надсилає запити daemon-у.

**Коротко:**

- Docker Client = команда `docker` у терміналі.
- Приймає команди користувача.
- Передає їх до Docker Daemon.

</details>

<details>
<summary>12. Як Docker Client взаємодіє з Docker Daemon?</summary>

#### Docker

Docker Client взаємодіє з daemon через Docker API:

- локально через Unix socket (типово `/var/run/docker.sock`);
- або віддалено через TCP (за належного захисту).

Коли ви виконуєте `docker ps`, CLI відправляє API-запит до daemon і повертає
результат у консоль.

**Коротко:**

- CLI -> API -> Daemon.
- Локально зазвичай використовується Unix socket.
- Daemon виконує дію й повертає відповідь.

</details>

<details>
<summary>13. Що таке Docker Host?</summary>

#### Docker

**Docker Host** — це машина (фізична або віртуальна), на якій встановлено
Docker Engine і де запускаються контейнери.

Host надає ресурси: CPU, RAM, disk, network.

**Коротко:**

- Docker Host — середовище виконання контейнерів.
- Може бути локальним ноутбуком або production-сервером.
- Контейнери ділять ресурси хоста.

</details>

<details>
<summary>14. Що таке Docker Registry?</summary>

#### Docker

**Docker Registry** — це сховище Docker-образів. У registry зберігаються
репозиторії та теги образів, які можна `push`/`pull`.

Registry буває публічним або приватним (Docker Hub, GHCR, ECR, GCR, Harbor).

**Коротко:**

- Registry зберігає і роздає образи.
- Підтримує версії через теги.
- Критичний компонент CI/CD.

</details>

<details>
<summary>15. Що таке Docker Hub?</summary>

#### Docker

**Docker Hub** — це публічний хмарний registry від Docker. Він містить:

- офіційні образи (`nginx`, `redis`, `postgres` тощо);
- образи від спільноти та команд;
- приватні репозиторії (на відповідних планах).

**Коротко:**

- Docker Hub — найпоширеніший registry за замовчуванням.
- Дозволяє швидко ділитися та отримувати образи.
- Часто використовується як source у CI/CD.

</details>

<details>
<summary>16. Як завантажити образ із Docker Hub?</summary>

#### Docker

Використовуйте команду `docker pull`:

```bash
docker pull nginx:latest
```

Якщо тег не вказати, за замовчуванням використовується `latest`.

```bash
docker pull redis
```

**Коротко:**

- Основна команда: `docker pull <image>:<tag>`.
- Без тега зазвичай береться `latest`.
- Після pull образ з'являється локально в кеші Docker.

</details>

<details>
<summary>17. Як запустити контейнер із образу?</summary>

#### Docker

Базовий запуск виконується через `docker run`:

```bash
docker run -d --name web -p 8080:80 nginx:latest
```

Тут:

- `-d` — фоновий режим;
- `--name web` — ім'я контейнера;
- `-p 8080:80` — проброс порту хост:контейнер.

**Коротко:**

- `docker run` створює і запускає контейнер.
- Параметри керують мережею, іменем, томами, env.
- Один із найважливіших базових Docker-команд.

</details>

<details>
<summary>18. Як переглянути список запущених контейнерів?</summary>

#### Docker

Для перегляду лише активних контейнерів використовуйте:

```bash
docker ps
```

Команда покаже ID, image, статус, порти, назву контейнера.

**Коротко:**

- `docker ps` показує тільки running-контейнери.
- Зручно для швидкої перевірки стану сервісів.
- Базова команда для operational рутини.

</details>

<details>
<summary>19. Як переглянути всі контейнери (включно із зупиненими)?</summary>

#### Docker

Використайте прапорець `-a`:

```bash
docker ps -a
```

Це покаже і запущені, і зупинені контейнери, включно з кодами завершення.

**Коротко:**

- `docker ps -a` показує повний список контейнерів.
- Допомагає діагностувати crash/exit після запуску.
- Часто використовується разом із `docker logs`.

</details>

<details>
<summary>20. Як зупинити контейнер?</summary>

#### Docker

Для коректної зупинки використовуйте `docker stop`:

```bash
docker stop web
```

Docker надсилає SIGTERM і чекає grace period, після чого може завершити процес
примусово.

**Коротко:**

- `docker stop <name|id>` — м'яка зупинка.
- Дає процесу час на graceful shutdown.
- Переважний спосіб завершення контейнера.

</details>

<details>
<summary>21. Як запустити зупинений контейнер?</summary>

#### Docker

Щоб знову запустити раніше створений контейнер, використовуйте:

```bash
docker start web
```

Це саме перезапуск існуючого контейнера, а не створення нового.

**Коротко:**

- `docker start` піднімає existing container.
- Конфігурація контейнера зберігається.
- Не плутати з `docker run` (створює новий).

</details>

<details>
<summary>22. Як примусово завершити контейнер?</summary>

#### Docker

Для негайного завершення використовується `docker kill`:

```bash
docker kill web
```

За замовчуванням надсилається SIGKILL, без graceful shutdown.

**Коротко:**

- `docker kill` зупиняє контейнер миттєво.
- Використовуйте, коли `stop` не спрацьовує.
- Може призвести до некоректного завершення процесів.

</details>

<details>
<summary>23. Як видалити контейнер?</summary>

#### Docker

Видалення контейнера:

```bash
docker rm web
```

Якщо контейнер запущений, спочатку зупиніть його, або видаляйте примусово:

```bash
docker rm -f web
```

**Коротко:**

- `docker rm` видаляє контейнер.
- Для running-контейнера потрібен `-f` або попередній `stop`.
- Видалення не зачіпає image.

</details>

<details>
<summary>24. Як видалити Docker Image?</summary>

#### Docker

Видалення образу виконується через `docker rmi`:

```bash
docker rmi nginx:latest
```

Якщо образ використовується контейнерами, спершу треба видалити/зупинити ці
контейнери.

**Коротко:**

- `docker rmi` видаляє локальний образ.
- Потрібно звільнити залежні контейнери.
- Корисно для очищення диска.

</details>

<details>
<summary>25. Як переглянути список образів?</summary>

#### Docker

Список локальних образів:

```bash
docker images
```

Альтернатива:

```bash
docker image ls
```

Команди показують repository, tag, image ID, розмір і дату створення.

**Коротко:**

- `docker images` / `docker image ls` показують локальні image.
- Допомагає контролювати кеш і зайнятий простір.
- Базова команда для повсякденної роботи з Docker.

</details>

<details>
<summary>26. Що таке Dockerfile?</summary>

#### Docker

**Dockerfile** — це текстовий файл з інструкціями для збірки Docker-образу.
Він описує базовий образ, кроки встановлення залежностей, копіювання коду,
конфігурацію середовища і команду запуску.

Dockerfile робить збірку повторюваною та версійованою.

**Коротко:**

- Dockerfile = рецепт збірки image.
- Дає відтворюваний build у локальному та CI середовищі.
- Є основою стандартизованого деплою.

</details>

<details>
<summary>27. Як створити Docker Image за допомогою Dockerfile?</summary>

#### Docker

Створення образу виконується командою `docker build` у директорії, де лежить
`Dockerfile`.

```bash
docker build -t my-app:1.0.0 .
```

Тут:

- `-t` задає `repository:tag`;
- `.` — build context (вміст каталогу, доступний під час збірки).

**Коротко:**

- Основна команда: `docker build -t <name>:<tag> <context>`.
- Docker читає інструкції з Dockerfile послідовно.
- Результат — локальний image, готовий до запуску або push.

</details>

<details>
<summary>28. Що таке інструкція FROM?</summary>

#### Docker

`FROM` задає базовий образ, з якого починається збірка.

```dockerfile
FROM node:20-alpine
```

У multi-stage build може бути кілька `FROM`, кожен відкриває окремий stage.

**Коротко:**

- `FROM` визначає базу для image.
- Без `FROM` Dockerfile зазвичай невалідний.
- Кілька `FROM` використовують для multi-stage збірки.

</details>

<details>
<summary>29. Що робить інструкція RUN?</summary>

#### Docker

`RUN` виконує команду під час **збірки** образу і створює новий layer.

```dockerfile
RUN apk add --no-cache curl
```

Типові use-case: встановлення пакетів, збірка артефактів, підготовка
файлової системи.

**Коротко:**

- `RUN` працює на етапі build, не runtime.
- Кожен `RUN` додає новий layer.
- Використовується для підготовки image.

</details>

<details>
<summary>30. Чим відрізняються RUN, CMD і ENTRYPOINT?</summary>

#### Docker

Ці інструкції працюють на різних етапах:

- `RUN` — команда під час **build** (формує image).
- `CMD` — команда за замовчуванням під час **run** (можна перевизначити).
- `ENTRYPOINT` — фіксована точка входу контейнера (аргументи часто додаються
  через `CMD` або CLI).

**Коротко:**

- `RUN` = build-time.
- `CMD`/`ENTRYPOINT` = runtime.
- `ENTRYPOINT` задає executable, `CMD` — дефолтні аргументи/команду.

</details>

<details>
<summary>31. Чим відрізняються CMD і ENTRYPOINT?</summary>

#### Docker

`CMD` задає дефолтну команду, яку легко замінити при `docker run`.
`ENTRYPOINT` задає основний процес контейнера, який зазвичай не замінюється,
а доповнюється аргументами.

Поширений шаблон:

- `ENTRYPOINT` — стабільний binary/script;
- `CMD` — дефолтні параметри запуску.

**Коротко:**

- `CMD` легко override-иться.
- `ENTRYPOINT` фіксує головний процес контейнера.
- Разом дають передбачуваний і гнучкий запуск.

</details>

<details>
<summary>32. Чим відрізняються COPY і ADD?</summary>

#### Docker

`COPY` просто копіює файли/теки з build context у image.
`ADD` робить більше: може розпаковувати локальні tar-архіви і працювати з URL
(хоча URL-скачування краще робити явно через `RUN curl/wget`).

У більшості випадків рекомендують `COPY` як більш передбачуваний варіант.

**Коротко:**

- `COPY` — базове та рекомендоване копіювання.
- `ADD` має додаткову "магію" (tar/URL).
- Якщо не потрібні спецможливості, обирайте `COPY`.

</details>

<details>
<summary>33. Що таке `.dockerignore` і навіщо він потрібен?</summary>

#### Docker

`.dockerignore` — файл, який виключає файли/каталоги з build context.

Приклад:

```txt
.git
node_modules
*.log
.env
```

Це пришвидшує збірку, зменшує розмір контексту і знижує ризик випадково
потрапити в image секретам або зайвим артефактам.

**Коротко:**

- `.dockerignore` фільтрує файли, що відправляються в build context.
- Покращує швидкість build і безпеку.
- Особливо важливий для великих репозиторіїв.

</details>

<details>
<summary>34. Що таке багатошарова архітектура Docker Image?</summary>

#### Docker

Docker Image складається з шарів (layers), де кожна інструкція Dockerfile
(наприклад `RUN`, `COPY`) додає новий шар.

Шари кешуються і перевикористовуються між збірками та контейнерами, що робить
build швидшим і економить місце.

**Коротко:**

- Image складається з послідовності layers.
- Layers immutable і кешуються.
- Правильний порядок інструкцій суттєво впливає на швидкість build.

</details>

<details>
<summary>35. Що таке layer у Docker?</summary>

#### Docker

**Layer** — це незмінний файловий шар образу, створений окремою інструкцією
збірки. Під час запуску контейнера Docker додає зверху writable layer для
runtime-змін.

Це дозволяє ефективно ділити спільні базові шари між багатьма образами.

**Коротко:**

- Layer — immutable частина image.
- Контейнер має додатковий writable layer.
- Шари перевикористовуються і економлять disk space.

</details>

<details>
<summary>36. Що таке multi-stage build?</summary>

#### Docker

**Multi-stage build** — підхід, коли в одному Dockerfile є кілька стадій збірки:
окрема для компіляції, окрема для фінального runtime-образу.

Приклад ідеї: зібрати бінарник у "builder" stage і скопіювати лише артефакт у
мінімальний runtime-образ.

**Коротко:**

- Дає менші й безпечніші фінальні image.
- Виносить build-залежності за межі production image.
- Стандартний підхід для modern Docker builds.

</details>

<details>
<summary>37. Як зменшити розмір Docker Image?</summary>

#### Docker

Практичні кроки:

1. Обирати легкі базові образи (`-alpine`, slim-варіанти).
2. Використовувати multi-stage build.
3. Копіювати тільки потрібні файли (`COPY` + `.dockerignore`).
4. Об'єднувати команди встановлення й чистити кеш пакетного менеджера.
5. Не класти в image тести, сорси збірки, тимчасові файли.

**Коротко:**

- Найбільший ефект дають base image + multi-stage.
- Контролюйте build context через `.dockerignore`.
- Менший image = швидший pull, краща безпека, дешевший storage.

</details>

<details>
<summary>38. Що таке dangling images і як їх видалити?</summary>

#### Docker

**Dangling images** — це "висячі" образи без тега (`<none>:<none>`), які
зазвичай лишаються після перебудов або ретегування.

Перегляд:

```bash
docker images -f dangling=true
```

Видалення:

```bash
docker image prune -f
```

**Коротко:**

- Dangling image не має нормального тега.
- Може непомітно займати багато диска.
- Очищується командою `docker image prune`.

</details>

<details>
<summary>39. Які стани може мати Docker-контейнер?</summary>

#### Docker

Типові стани контейнера в Docker:

- `created` — контейнер створений, але не запущений;
- `running` — контейнер виконується;
- `paused` — процеси призупинені;
- `restarting` — йде перезапуск;
- `exited` — контейнер зупинений;
- `dead` — контейнер у некоректному стані (зазвичай після помилки).

**Коротко:**

- Контейнер проходить кілька runtime-станів.
- Найчастіші у практиці: `running` і `exited`.
- Стан легко перевірити через `docker ps -a`.

</details>

<details>
<summary>40. Опишіть життєвий цикл контейнера.</summary>

#### Docker

Типовий життєвий цикл:

1. Створення контейнера (`docker create` або `docker run`).
2. Запуск (`docker start` або одразу в `run`).
3. Робота процесу в стані `running`.
4. Зупинка (`docker stop`/`docker kill`) -> стан `exited`.
5. Повторний запуск (`docker start`) або видалення (`docker rm`).

Опціонально можливі `pause/unpause`, `restart`, політики автоперезапуску.

**Коротко:**

- Create -> Run -> Stop -> Start/Remove.
- Контейнер зазвичай ефемерний елемент інфраструктури.
- Дані для довгого зберігання виносять у volumes.

</details>

<details>
<summary>41. Що робить команда `docker create`?</summary>

#### Docker

`docker create` створює контейнер з image, але **не запускає** його.

```bash
docker create --name app nginx:latest
```

Після цього контейнер буде у стані `created` і його можна запустити окремо:

```bash
docker start app
```

**Коротко:**

- `docker create` = підготовка контейнера без старту.
- Дозволяє розділити етапи create і start.
- Використовується рідше, ніж `docker run`.

</details>

<details>
<summary>42. Що відбувається під час `docker stop`?</summary>

#### Docker

`docker stop` виконує graceful shutdown:

1. Docker надсилає головному процесу контейнера сигнал `SIGTERM`.
2. Чекає заданий timeout (типово ~10 секунд).
3. Якщо процес не завершився — надсилає `SIGKILL`.

```bash
docker stop app
```

**Коротко:**

- `docker stop` спочатку дає шанс завершитися коректно.
- Лише після timeout застосовується жорстке завершення.
- Рекомендований спосіб зупинки сервісів.

</details>

<details>
<summary>43. Чим відрізняються `docker stop` і `docker kill`?</summary>

#### Docker

Різниця в сигналах і поведінці:

- `docker stop` -> `SIGTERM` + очікування + за потреби `SIGKILL`.
- `docker kill` -> одразу `SIGKILL` (або інший сигнал, якщо вказати).

`stop` безпечніший для більшості застосунків, бо дає шанс зберегти стан і
закрити з'єднання.

**Коротко:**

- `stop` = м'яко, `kill` = негайно.
- Для production спочатку використовують `stop`.
- `kill` застосовують, коли контейнер "завис".

</details>

<details>
<summary>44. Що робить команда `docker restart`?</summary>

#### Docker

`docker restart` послідовно зупиняє і знову запускає контейнер.

```bash
docker restart app
```

Поведінка схожа на `stop` + `start`: спочатку graceful stop, потім новий старт
того ж контейнера.

**Коротко:**

- `docker restart` = швидкий перезапуск контейнера.
- Використовує той самий контейнер, а не створює новий.
- Зручно після зміни зовнішніх залежностей або тимчасових збоїв.

</details>

<details>
<summary>45. Чи може контейнер автоматично перезапускатися?</summary>

#### Docker

Так. Для цього задають `restart policy` під час запуску контейнера.

```bash
docker run -d --restart unless-stopped --name app nginx:latest
```

Policy визначає, коли Docker має автоматично підняти контейнер після падіння,
рестарту Docker daemon або перезавантаження хоста.

**Коротко:**

- Автоперезапуск підтримується вбудовано.
- Налаштовується через `--restart`.
- Важливий для підвищення доступності сервісу.

</details>

<details>
<summary>46. Які існують restart policy (`no`, `on-failure`, `always`, `unless-stopped`)?</summary>

#### Docker

Основні restart policy:

- `no` — не перезапускати автоматично (значення за замовчуванням).
- `on-failure[:max-retries]` — перезапускати лише якщо процес завершився з
  помилкою (non-zero exit code).
- `always` — завжди перезапускати контейнер після зупинки/рестарту daemon.
- `unless-stopped` — як `always`, але якщо контейнер зупинено вручну, Docker не
  підніматиме його автоматично після рестарту daemon/хоста.

**Коротко:**

- `no` — без автоперезапуску.
- `on-failure` — тільки при падінні.
- `always`/`unless-stopped` — для long-running сервісів.

</details>

<details>
<summary>47. Чи зберігаються дані після зупинки контейнера?</summary>

#### Docker

Так. Після `docker stop` дані у writable layer контейнера залишаються, бо
контейнер лише зупиняється, а не видаляється.

Якщо потім виконати `docker start`, стан файлової системи контейнера збережеться.

**Коротко:**

- `stop` не видаляє дані контейнера.
- Дані зникають не при зупинці, а при видаленні контейнера.
- Для важливих даних краще використовувати volumes.

</details>

<details>
<summary>48. Коли дані контейнера можуть бути втрачені?</summary>

#### Docker

Дані можуть бути втрачені, якщо вони зберігались тільки у writable layer і:

- контейнер видалили (`docker rm`);
- контейнер перевидали після оновлення image;
- виконали очищення, що зачепило контейнерні шари.

Щоб уникнути втрат, стан потрібно виносити у `volume` або `bind mount`.

**Коротко:**

- Ризик втрати: видалення/пересоздання контейнера.
- Ephemeral storage не підходить для критичних даних.
- Persistency забезпечують volumes або зовнішні сховища.

</details>

<details>
<summary>49. Що таке Docker Volume?</summary>

#### Docker

**Docker Volume** — це кероване Docker сховище для персистентних даних.
Volume живе окремо від життєвого циклу контейнера.

Його використовують для БД, логів, кешів та будь-яких даних, що мають переживати
перезапуски і перевипуск контейнерів.

**Коротко:**

- Volume = постійне сховище даних.
- Не зникає при видаленні контейнера (доки не видалений окремо).
- Рекомендований спосіб зберігання стану в Docker.

</details>

<details>
<summary>50. Де зберігаються Docker Volumes на хості?</summary>

#### Docker

У Linux типово volumes зберігаються в каталозі:

```txt
/var/lib/docker/volumes/
```

Для Docker Desktop (macOS/Windows) фактичне зберігання відбувається всередині
Linux VM, яку використовує Docker Desktop.

**Коротко:**

- Linux default path: `/var/lib/docker/volumes/`.
- У Desktop шляхи абстраговані через внутрішню VM.
- Краще керувати volume через Docker-команди, а не вручну.

</details>

<details>
<summary>51. Що таке bind mount?</summary>

#### Docker

**Bind mount** підключає конкретний шлях хоста в контейнер.

```bash
docker run -v /host/path:/app/data nginx:latest
```

Контейнер читає/пише напряму в цю директорію хоста.

**Коротко:**

- Bind mount = прямий мапінг шляху хоста.
- Зручний для dev-сценаріїв (live code, конфіги).
- Сильна залежність від структури файлової системи хоста.

</details>

<details>
<summary>52. Чим Volume відрізняється від bind mount?</summary>

#### Docker

Різниця:

- `Volume` керується Docker і portable між хостами на рівні Docker abstractions.
- `Bind mount` прив'язаний до конкретного шляху ОС хоста.

`Volume` зазвичай кращий для production-даних, `bind mount` — для локальної
розробки та явного доступу до файлів хоста.

**Коротко:**

- Volume: керований Docker, зручний для persistent data.
- Bind mount: прямий шлях хоста, більше гнучкості й більше ризиків.
- Для БД у production частіше обирають volume.

</details>

<details>
<summary>53. Як поділитися даними між контейнерами?</summary>

#### Docker

Найпоширеніший варіант — підключити один і той самий volume до кількох
контейнерів.

```bash
docker volume create shared-data
docker run -d --name c1 -v shared-data:/data nginx
docker run -d --name c2 -v shared-data:/data busybox
```

Також можливий bind mount того самого хост-шляху.

**Коротко:**

- Спільний volume дає обмін файлами між контейнерами.
- Це стандартний патерн для sidecar/backup задач.
- Потрібно враховувати конкуренцію записів і блокування.

</details>

<details>
<summary>54. Як працює мережа в Docker?</summary>

#### Docker

Docker створює віртуальні мережі і підключає до них контейнери через network
namespaces та драйвери (bridge, host, overlay тощо).

Кожен контейнер отримує мережевий інтерфейс, IP і маршрути в межах своєї мережі.
Проброс портів (`-p`) відкриває доступ із хоста назовні.

**Коротко:**

- Контейнери ізольовані по мережі.
- Комунікація керується Docker network driver.
- Публічний доступ робиться через port mapping.

</details>

<details>
<summary>55. Який мережевий драйвер використовується за замовчуванням?</summary>

#### Docker

Для standalone-контейнерів за замовчуванням використовується `bridge` мережа
(`bridge` network типу `docker0` на Linux).

Якщо не вказати `--network`, контейнер буде підключений до default bridge.

**Коротко:**

- Default driver для звичайного `docker run` — `bridge`.
- Дає базову ізоляцію та внутрішню IP-комунікацію.
- Для керованої взаємодії краще створювати user-defined bridge.

</details>

<details>
<summary>56. Які типи мереж існують у Docker (bridge, host, overlay, macvlan, none)?</summary>

#### Docker

Основні типи:

- `bridge` — стандартна мережа для контейнерів на одному хості.
- `host` — контейнер використовує мережевий стек хоста.
- `overlay` — мережа між кількома хостами (Swarm).
- `macvlan` — контейнер отримує MAC/IP у фізичній мережі.
- `none` — мережа відключена.

**Коротко:**

- Кожен драйвер вирішує різні network-задачі.
- `bridge` найпоширеніший для локальних/одиночних хостів.
- `overlay` потрібен для multi-host сценаріїв.

</details>

<details>
<summary>57. Що таке bridge-мережа?</summary>

#### Docker

`Bridge` — віртуальна L2-мережа на одному Docker host, де контейнери можуть
спілкуватися між собою.

User-defined bridge надає вбудований DNS по іменах контейнерів і кращу керованість.

**Коротко:**

- Bridge об'єднує контейнери в межах одного хоста.
- Дозволяє внутрішню комунікацію без зовнішнього доступу.
- User-defined bridge кращий за default bridge.

</details>

<details>
<summary>58. Що таке host-мережа?</summary>

#### Docker

У режимі `host` контейнер не отримує окремий мережевий namespace, а використовує
мережу хоста напряму.

Через це немає NAT і port mapping, але ізоляція мережі зменшується.

**Коротко:**

- `--network host` дає нативний мережевий стек хоста.
- Може зменшити network overhead.
- Компроміс: нижча ізоляція і вищі ризики конфлікту портів.

</details>

<details>
<summary>59. Що таке overlay-мережа?</summary>

#### Docker

`Overlay` — віртуальна мережа для контейнерів на різних хостах, зазвичай у
Docker Swarm.

Вона інкапсулює трафік і дає сервісам прозоро спілкуватися між вузлами, ніби
вони в одній мережі.

**Коротко:**

- Overlay = multi-host мережа.
- Ключовий інструмент для кластерних Docker-сценаріїв.
- Найчастіше використовується разом зі Swarm.

</details>

<details>
<summary>60. Як створити власну Docker-мережу?</summary>

#### Docker

Створення user-defined bridge мережі:

```bash
docker network create app-net
```

Запуск контейнера в ній:

```bash
docker run -d --name api --network app-net nginx
```

**Коротко:**

- Використовуйте `docker network create`.
- User-defined мережі дають DNS і кращу ізоляцію.
- Рекомендований підхід для сервісів, що взаємодіють між собою.

</details>

<details>
<summary>61. Як контейнери знаходять один одного в мережі?</summary>

#### Docker

У user-defined мережах Docker надає вбудований DNS. Контейнери можуть звертатися
один до одного за іменем контейнера або alias.

Приклад: сервіс `api` може викликати `db:5432`, якщо обидва в одній мережі.

**Коротко:**

- Service discovery працює через внутрішній DNS Docker.
- Ім'я контейнера часто є DNS-ім'ям у мережі.
- Потрібно, щоб контейнери були підключені до однієї мережі.

</details>

<details>
<summary>62. Що таке namespaces у Docker?</summary>

#### Docker

`Namespaces` — механізм Linux kernel для ізоляції ресурсів процесів. Docker
використовує `pid`, `net`, `mnt`, `ipc`, `uts`, `user` namespaces.

Завдяки цьому контейнер "бачить" власний набір процесів, мереж, hostname,
монтувань тощо.

**Коротко:**

- Namespaces забезпечують логічну ізоляцію.
- Кожен контейнер має свій ізольований view системи.
- Це фундамент контейнеризації в Linux.

</details>

<details>
<summary>63. Що таке cgroups?</summary>

#### Docker

`cgroups` (control groups) — механізм Linux kernel для обмеження й обліку
ресурсів процесів: CPU, RAM, I/O, pids.

Docker використовує cgroups, щоб один контейнер не "з'їв" усі ресурси хоста.

**Коротко:**

- cgroups = контроль ресурсів.
- Дають ліміти і fair sharing між контейнерами.
- Критично важливі для стабільності production.

</details>

<details>
<summary>64. Як Docker ізолює контейнери?</summary>

#### Docker

Ізоляція базується на комбінації механізмів Linux:

- namespaces (ізоляція оточення);
- cgroups (ліміти ресурсів);
- capabilities, seccomp, AppArmor/SELinux (безпека);
- окремі filesystem layers і мережі.

**Коротко:**

- Docker не запускає повну гостьову ОС, але ізолює процеси ядром Linux.
- Ізоляція багаторівнева: процеси, мережа, ФС, права.
- Безпека залежить і від конфігурації контейнера.

</details>

<details>
<summary>65. Чому Docker потребує Linux kernel?</summary>

#### Docker

Docker relies on Linux kernel features (`namespaces`, `cgroups`, capabilities),
які і реалізують контейнерну ізоляцію.

Тому нативно Docker працює на Linux. Інші ОС використовують Linux VM або
kernel-compatible шари для контейнерного runtime.

**Коротко:**

- Контейнери Docker побудовані на Linux kernel primitives.
- Без них стандартна модель Docker не працює.
- Linux — нативне середовище для Docker runtime.

</details>

<details>
<summary>66. Як Docker працює на Windows і macOS?</summary>

#### Docker

На macOS і більшості сценаріїв Windows Docker Desktop запускає легку Linux VM,
всередині якої працює Docker Engine.

Користувач працює з тим самим CLI/API, але фактичний runtime контейнерів — у VM.
На Windows також існують Windows-containers для відповідних образів.

**Коротко:**

- На не-Linux ОС Docker зазвичай працює через Linux VM.
- CLI для користувача виглядає так само.
- Важливо враховувати різницю файлової системи та продуктивності mount.

</details>

<details>
<summary>67. Що таке containerd?</summary>

#### Docker

`containerd` — це контейнерний runtime-демон, який керує життєвим циклом
контейнерів, image pull/push, snapshot та storage операціями.

Docker використовує `containerd` під капотом як нижчий runtime шар.

**Коротко:**

- containerd — core runtime компонент.
- Відповідає за low-level container operations.
- Використовується не лише Docker, а й іншими платформами.

</details>

<details>
<summary>68. Чим containerd відрізняється від dockerd?</summary>

#### Docker

- `dockerd` — високорівневий Docker daemon (API, build, networks, volumes,
  інтеграція CLI).
- `containerd` — нижчий runtime шар для виконання контейнерів.

Спрощено: `dockerd` оркеструє Docker-функціональність, `containerd` виконує
runtime-операції.

**Коротко:**

- `dockerd` = верхній рівень Docker платформи.
- `containerd` = runtime фундамент під ним.
- Обидва працюють разом у стандартній Docker-архітектурі.

</details>

<details>
<summary>69. Що таке runC?</summary>

#### Docker

`runC` — низькорівневий OCI runtime, який безпосередньо створює і запускає
контейнерні процеси згідно OCI-специфікації.

У типовому стеку Docker виклики йдуть зверху вниз: `dockerd` -> `containerd` ->
`runC`.

**Коротко:**

- runC виконує фактичний запуск контейнера.
- OCI-сумісний компонент низького рівня.
- Зазвичай використовується через containerd, а не напряму.

</details>

<details>
<summary>70. Як обмежити CPU і пам’ять для контейнера?</summary>

#### Docker

При запуску задають ресурсні ліміти:

```bash
docker run -d --name app --cpus="1.5" --memory="512m" --memory-swap="512m" nginx
```

Також часто використовують `--pids-limit`, `--cpu-shares`, `--cpuset-cpus`.

**Коротко:**

- Ліміти задаються параметрами `docker run`.
- Мінімум для production: ліміт RAM і CPU.
- Це захищає хост від "шумних" контейнерів.

</details>

<details>
<summary>71. Як перевірити використання ресурсів контейнера?</summary>

#### Docker

Швидкий перегляд runtime-метрик:

```bash
docker stats
```

Для конкретного контейнера:

```bash
docker stats app
```

Команда показує CPU, RAM, network I/O, block I/O.

**Коротко:**

- `docker stats` — базовий live-моніторинг.
- Дає оперативну картину по навантаженню контейнерів.
- Для production бажано підключати зовнішню observability.

</details>

<details>
<summary>72. Як переглянути логи контейнера?</summary>

#### Docker

Використовуйте `docker logs`:

```bash
docker logs app
```

Стрім логів у реальному часі:

```bash
docker logs -f --tail 100 app
```

**Коротко:**

- `docker logs` читає stdout/stderr контейнера.
- `-f` для follow, `--tail` для останніх рядків.
- У production логи краще централізувати.

</details>

<details>
<summary>73. Як підключитися всередину контейнера?</summary>

#### Docker

Для інтерактивної сесії:

```bash
docker exec -it app sh
```

Або `bash`, якщо він є в образі:

```bash
docker exec -it app bash
```

**Коротко:**

- `docker exec -it` запускає shell у running-контейнері.
- Зручно для діагностики й дебагу.
- Не варто робити manual-fixes як постійну практику.

</details>

<details>
<summary>74. Як отримати детальну інформацію про контейнер або image?</summary>

#### Docker

Для детальної JSON-інформації використовують `docker inspect`:

```bash
docker inspect app
docker inspect nginx:latest
```

Там є конфіг, мережа, mounts, env, статус, metadata.

**Коротко:**

- `docker inspect` дає повний технічний стан об'єкта.
- Працює для container, image, network, volume.
- Основний інструмент для troubleshooting.

</details>

<details>
<summary>75. Що робить команда `docker system prune`?</summary>

#### Docker

`docker system prune` очищає невикористовувані Docker-ресурси:

- stopped containers;
- unused networks;
- dangling images;
- build cache.

```bash
docker system prune -f
```

**Коротко:**

- Видаляє непотрібні артефакти і звільняє диск.
- Потребує обережності в production.
- Для ширшого очищення існують додаткові прапорці (`-a`, `--volumes`).

</details>

<details>
<summary>76. Як моніторити Docker у production?</summary>

#### Docker

Практичний підхід:

1. Збирати метрики контейнерів/хоста (CPU, RAM, restarts, fs, network).
2. Централізувати логи.
3. Налаштувати алерти по SLO/SLA (latency, error rate, OOM, crash-loop).
4. Мати дашборди по сервісах і вузлах.

Типовий стек: Prometheus + Grafana + Alertmanager + Loki/ELK.

**Коротко:**

- Потрібен моніторинг і контейнерів, і хостів.
- Критичні сигнали: OOM, restart spikes, saturation ресурсів.
- Без алертингу моніторинг не закриває production-ризики.

</details>

<details>
<summary>77. Як реалізувати healthcheck для контейнера?</summary>

#### Docker

Healthcheck задають у Dockerfile або при `docker run`.

```dockerfile
HEALTHCHECK --interval=30s --timeout=3s --retries=3 \
  CMD wget -qO- http://localhost:8080/health || exit 1
```

Docker відмічає контейнер як `healthy` або `unhealthy` за результатом команди.

**Коротко:**

- Healthcheck дає сигнал про фактичну готовність сервісу.
- Краще використовувати lightweight endpoint.
- Важливий для автоматичного відновлення і оркестрації.

</details>

<details>
<summary>78. Як забезпечити безпеку контейнерів?</summary>

#### Docker

Базові практики:

- використовувати мінімальні базові образи;
- не запускати процеси від root (`USER`);
- обмежувати capabilities, застосовувати `seccomp`/AppArmor/SELinux;
- сканувати image на вразливості;
- підписувати й контролювати джерела образів;
- оновлювати image і runtime регулярно.

**Коротко:**

- Безпека починається з supply chain образів.
- Принцип least privilege обов'язковий.
- Сканування та патч-менеджмент мають бути регулярними.

</details>

<details>
<summary>79. Як працювати із секретами в Docker?</summary>

#### Docker

Секрети не слід вшивати в image або комітити в git.

Підходи:

- передавати через зовнішній secret manager;
- у Swarm — використовувати Docker Secrets;
- у Compose/dev — передавати через env/file, але з обережністю.

Для production краще short-lived credentials і ротація.

**Коротко:**

- Секрети мають приходити на runtime, не на build-time image.
- Перевага за централізованими secret manager рішеннями.
- Ротація і аудит доступу обов'язкові.

</details>

<details>
<summary>80. Що таке Docker Compose?</summary>

#### Docker

**Docker Compose** — інструмент для опису і запуску multi-container застосунків
через декларативний YAML-файл.

В одному файлі задають сервіси, мережі, томи, env, залежності.

**Коротко:**

- Compose = "інфраструктура застосунку" в одному файлі.
- Спрощує запуск кількох сервісів однією командою.
- Дуже зручний для dev/test середовищ.

</details>

<details>
<summary>81. Для чого використовується Docker Compose?</summary>

#### Docker

Compose застосовують для:

- локального запуску стеку (app + db + cache + queue);
- інтеграційних тестів;
- стандартизованого dev environment у команді;
- швидкого підняття демо/POC.

**Коротко:**

- Compose описує і піднімає весь стек сервісів.
- Мінімізує ручні команди `docker run`.
- Основний інструмент локальної контейнерної оркестрації.

</details>

<details>
<summary>82. Чим Docker Compose відрізняється від Dockerfile?</summary>

#### Docker

- `Dockerfile` описує, **як зібрати один image**.
- `Compose` описує, **як запустити та зв'язати кілька контейнерів**.

Вони доповнюють одне одного, а не заміняють.

**Коротко:**

- Dockerfile = build-рівень.
- Compose = runtime-рівень multi-service застосунку.
- У типовому проєкті використовують обидва.

</details>

<details>
<summary>83. Яка структура файлу `docker-compose.yml`?</summary>

#### Docker

Типова структура:

- `services` — контейнери застосунку;
- `networks` — мережі між сервісами;
- `volumes` — персистентні сховища;
- опційно `configs`, `secrets` (залежно від режиму/платформи).

**Коротко:**

- Ядро Compose-файлу: `services`, `networks`, `volumes`.
- YAML декларативно описує стан стеку.
- Один файл часто достатній для dev середовища.

</details>

<details>
<summary>84. Що таке services у Docker Compose?</summary>

#### Docker

`services` — це логічні компоненти застосунку (наприклад `web`, `db`, `redis`),
кожен з власним image/build, портами, env, volumes і policy.

Compose створює для кожного сервісу один або кілька контейнерів.

**Коротко:**

- Service описує роль і конфіг контейнера.
- Кожен сервіс має власні параметри запуску.
- Сервіси разом формують повний стек застосунку.

</details>

<details>
<summary>85. Що таке networks у Docker Compose?</summary>

#### Docker

`networks` у Compose визначають, як сервіси спілкуються між собою і які з них
ізольовані.

За замовчуванням Compose створює окрему project-мережу, де сервіси доступні за
іменами.

**Коротко:**

- Networks керують зв'язністю та ізоляцією сервісів.
- Compose автоматично створює default network.
- Для складних схем можна оголосити кілька мереж.

</details>

<details>
<summary>86. Що таке volumes у Docker Compose?</summary>

#### Docker

`volumes` у Compose — декларативний опис персистентних сховищ, які монтуються в
сервіси.

Приклад: винести дані PostgreSQL у named volume, щоб вони не губилися після
перезапуску контейнера.

**Коротко:**

- Volumes у Compose дають persistency для стану.
- Оголошуються один раз і підключаються до сервісів.
- Критично важливі для БД і stateful компонентів.

</details>

<details>
<summary>87. Як запустити застосунок через Docker Compose?</summary>

#### Docker

Сучасний синтаксис:

```bash
docker compose up -d
```

Команда збирає (за потреби), створює мережі/томи і запускає сервіси у фоні.

**Коротко:**

- Основна команда: `docker compose up -d`.
- Піднімає весь стек з `docker-compose.yml`.
- Для розробки часто використовують `docker compose up` без `-d`.

</details>

<details>
<summary>88. Що робить команда `docker-compose down`?</summary>

#### Docker

`docker-compose down` (або `docker compose down`) зупиняє і видаляє контейнери,
мережі та інші ресурси, створені `up`.

За замовчуванням named volumes не видаляються, якщо не вказати `-v`.

**Коротко:**

- `down` прибирає стек, створений Compose.
- Очищає контейнери й мережі проєкту.
- Для видалення томів використовуйте `-v`.

</details>

<details>
<summary>89. Як сервіси взаємодіють між собою в Compose?</summary>

#### Docker

Сервіси, що в одній Compose-мережі, звертаються один до одного по імені сервісу
і внутрішньому порту.

Наприклад, `web` може підключатись до `db:5432` без публікації цього порту назовні.

**Коротко:**

- Взаємодія відбувається через internal network.
- Ім'я сервісу = DNS-ім'я.
- Публічний порт потрібен лише для зовнішнього доступу.

</details>

<details>
<summary>90. Як працює DNS між сервісами?</summary>

#### Docker

Compose використовує вбудований DNS Docker. Для кожного сервісу реєструється
ім'я, яке резолвиться в IP контейнера в межах мережі.

При масштабуванні сервісу DNS може повертати кілька IP (round-robin).

**Коротко:**

- DNS автоматично доступний у межах Compose-мережі.
- Сервіси знаходять один одного за service name.
- Не потрібно вручну прописувати IP адреси.

</details>

<details>
<summary>91. Що таке `depends_on`?</summary>

#### Docker

`depends_on` — директива Compose, що керує порядком запуску/зупинки сервісів.

Вона каже Compose, що один сервіс логічно залежить від іншого.

**Коротко:**

- `depends_on` визначає startup order.
- Допомагає уникнути хаотичного старту стеку.
- Не є повноцінною перевіркою готовності.

</details>

<details>
<summary>92. Чому `depends_on` не гарантує готовність сервісу?</summary>

#### Docker

Тому що "контейнер запущений" не означає "застосунок всередині готовий приймати
запити".

Наприклад, БД може стартувати контейнер, але ще виконувати ініціалізацію.

**Коротко:**

- `depends_on` гарантує порядок, але не readiness.
- Потрібні healthchecks або wait-механізми.
- Інакше можливі race conditions на старті.

</details>

<details>
<summary>93. Як реалізувати очікування готовності сервісу?</summary>

#### Docker

Найпрактичніше:

1. Додати `healthcheck` для залежного сервісу (наприклад БД).
2. Використовувати механізм очікування в клієнтському сервісі (`wait-for-it`,
   `dockerize`, retry loop у коді).

Production-friendly підхід — retries з backoff на рівні застосунку.

**Коротко:**

- Readiness вирішується не тільки Compose-конфігом, а й логікою сервісу.
- Healthcheck + retry/backoff дають стабільний старт.
- Це зменшує флейки в CI/CD та локальному dev.

</details>

<details>
<summary>94. Як використовувати змінні середовища в Compose?</summary>

#### Docker

У `docker-compose.yml` змінні підставляються як `${VAR}` і можуть передаватись у
`environment`.

Приклад:

```yaml
services:
  app:
    environment:
      - DB_HOST=${DB_HOST}
      - DB_PORT=${DB_PORT}
```

**Коротко:**

- Compose підтримує шаблонізацію через `${...}`.
- Значення приходять із shell або `.env`.
- Це дозволяє мати різні конфіги без дублювання файлів.

</details>

<details>
<summary>95. Як працює файл `.env`?</summary>

#### Docker

Файл `.env` поруч із compose-файлом містить пари `KEY=VALUE`, які Compose
використовує для підстановки змінних.

```txt
DB_HOST=db
DB_PORT=5432
```

`.env` зручний для локальної конфігурації, але секрети для production краще
тримати у спеціалізованих secret manager рішеннях.

**Коротко:**

- `.env` підживлює змінні для Compose-шаблонів.
- Спрощує перемикання між середовищами.
- Не ідеальний для чутливих production-секретів.

</details>

<details>
<summary>96. Як використовувати кілька Compose-файлів (dev/prod)?</summary>

#### Docker

Compose дозволяє накладати файли один на один.

```bash
docker compose -f docker-compose.yml -f docker-compose.dev.yml up -d
docker compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

Базовий файл містить спільну конфігурацію, override-файли — відмінності
конкретного середовища.

**Коротко:**

- Multi-file підхід зменшує дублювання конфігів.
- Base + overrides = чиста структура dev/prod.
- Порядок `-f` важливий (пізніші файли перекривають попередні).

</details>

<details>
<summary>97. Як масштабувати сервіси через Compose?</summary>

#### Docker

Масштабування виконується через `--scale`:

```bash
docker compose up -d --scale web=3
```

Compose підніме кілька реплік сервісу. Потрібно врахувати балансування трафіку
і stateful обмеження.

**Коротко:**

- `--scale service=N` створює кілька контейнерів сервісу.
- Підходить для stateless-компонентів.
- Для складного production-автоскейлу зазвичай потрібен оркестратор.

</details>

<details>
<summary>98. Як організувати healthcheck у Docker Compose?</summary>

#### Docker

Healthcheck задається в секції сервісу:

```yaml
services:
  api:
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:8080/health"]
      interval: 30s
      timeout: 3s
      retries: 3
      start_period: 10s
```

Це дозволяє відстежувати стан сервісу і використовувати readiness у сценаріях
залежностей та моніторингу.

**Коротко:**

- Healthcheck у Compose описується прямо в `service`.
- Дає статус `healthy/unhealthy`.
- Потрібен для надійного керування залежностями.

</details>

<details>
<summary>99. Які обмеження Docker Compose у production?</summary>

#### Docker

Compose має обмеження для великого production:

- немає повноцінного scheduler-а по кластерах;
- обмежені вбудовані механізми self-healing і autoscaling;
- слабша історично інтеграція enterprise-рівня політик і multi-tenant контролю;
- складніше керувати великим distributed-флотом.

Для невеликих production-систем Compose може бути достатнім, але масштаб має
бути контрольованим.

**Коротко:**

- Compose сильний у dev/test і малому prod.
- Для великого кластера зазвичай обирають Swarm/Kubernetes.
- Межа застосування залежить від складності і SLO вимог.

</details>

<details>
<summary>100. Чим Docker Compose відрізняється від Docker Swarm або Kubernetes?</summary>

#### Docker

Порівняння:

- **Compose**: локальна/проста оркестрація, переважно single-host або невеликі
  сценарії.
- **Swarm**: вбудована кластерна оркестрація Docker з простішим operational
  порогом входу.
- **Kubernetes**: найпотужніша оркестрація для великих distributed-систем
  (autoscaling, self-healing, rich ecosystem, policy control).

**Коротко:**

- Compose — найпростіший рівень.
- Swarm/K8s — кластерний рівень оркестрації.
- Kubernetes зазвичай обирають для складного enterprise production.

</details>

<details>
<summary>101. Що таке Docker Swarm?</summary>

#### Docker

**Docker Swarm** — це вбудований у Docker режим кластерної оркестрації, що
об'єднує кілька Docker-хостів у єдиний кластер.

У Swarm є manager-вузли (керують станом кластера) і worker-вузли (виконують
сервіси/таски).

**Коротко:**

- Swarm = кластерний режим Docker.
- Дає оркестрацію сервісів на кількох вузлах.
- Простіший поріг входу, ніж у Kubernetes.

</details>

<details>
<summary>102. Як масштабувати сервіси у Docker Swarm?</summary>

#### Docker

Масштабування виконується зміною кількості реплік сервісу:

```bash
docker service scale web=5
```

Альтернатива через update:

```bash
docker service update --replicas 5 web
```

**Коротко:**

- Масштабування у Swarm = зміна `replicas`.
- Swarm сам розподіляє таски по вузлах.
- Підходить для stateless-сервісів.

</details>

<details>
<summary>103. Чи підтримує Swarm автоматичне масштабування?</summary>

#### Docker

Нативного horizontal autoscaling (на кшталт HPA) у Docker Swarm немає.

Swarm підтримує self-healing (перезапуск/перерозміщення тасків), але
автоматичне масштабування реплік за метриками зазвичай реалізують зовнішніми
скриптами/інструментами.

**Коротко:**

- Built-in autoscaling у Swarm відсутній.
- Є автоматичне відновлення сервісів, але не auto-replica scaling.
- Для autoscaling потрібні зовнішні механізми.

</details>

<details>
<summary>104. Як працює балансування навантаження у Swarm?</summary>

#### Docker

Swarm використовує routing mesh: запит може прийти на будь-який вузол кластера,
після чого буде проксійований до однієї з реплік сервісу.

Додатково є внутрішнє балансування між тасками сервісу через вбудований DNS/VIP.

**Коротко:**

- Swarm має вбудований load balancing.
- Routing mesh дозволяє доступ через будь-який node.
- Трафік розподіляється між репліками сервісу.

</details>

<details>
<summary>105. Як Docker використовується в CI/CD?</summary>

#### Docker

У CI/CD Docker зазвичай використовується так:

1. Зібрати image з коду.
2. Прогнати тести/скани.
3. Запушити image у registry.
4. Деплоїти конкретний тег/digest у середовище.

Це робить релізи відтворюваними і зменшує різницю між build та run середовищем.

**Коротко:**

- Docker стандартизує build artifact.
- Один image проходить шлях від CI до production.
- Зручно для rollback і traceability.

</details>

<details>
<summary>106. Як зберігати та версіонувати Docker Images?</summary>

#### Docker

Практика версіонування:

- використовувати semver/релізні теги (`1.4.2`);
- додавати immutable tag (наприклад git SHA);
- у деплої краще фіксувати digest (`@sha256:...`) для повної відтворюваності.

Зберігають image у registry з політиками retention та доступу.

**Коротко:**

- Не покладатися лише на `latest`.
- Мати зрозумілу tag-стратегію + immutable ідентифікатор.
- Для критичних релізів використовувати digest pinning.

</details>

<details>
<summary>107. Як пушити образ у Registry?</summary>

#### Docker

Кроки:

1. Затегувати image під registry/repo.
2. Авторизуватись.
3. Виконати push.

```bash
docker tag my-app:1.0.0 registry.example.com/team/my-app:1.0.0
docker push registry.example.com/team/my-app:1.0.0
```

**Коротко:**

- Потрібен правильний повний тег репозиторію.
- Без `docker login` push зазвичай не спрацює.
- Після push image доступний для деплою з registry.

</details>

<details>
<summary>108. Як виконати `docker login`?</summary>

#### Docker

Базова авторизація:

```bash
docker login
```

Для конкретного registry:

```bash
docker login registry.example.com
```

У CI краще використовувати token/robot account і non-interactive вхід через
stdin для пароля.

**Коротко:**

- `docker login` зберігає облікові дані для registry.
- Для CI використовуйте токени, не паролі користувачів.
- Мінімізуйте scope прав облікових даних.

</details>

<details>
<summary>109. Як експортувати та імпортувати Docker Image (`save/load`)?</summary>

#### Docker

Експорт image у tar:

```bash
docker save -o my-app.tar my-app:1.0.0
```

Імпорт назад:

```bash
docker load -i my-app.tar
```

Це корисно для air-gapped середовищ або офлайн-перенесення.

**Коротко:**

- `save` експортує image у файл.
- `load` відновлює image з tar.
- Зручно, коли registry недоступний.

</details>

<details>
<summary>110. Як організувати multi-environment (dev/stage/prod) з Docker?</summary>

#### Docker

Практичний підхід:

- один базовий Dockerfile;
- різні конфіги через env vars/secrets;
- різні compose/stack-файли або overlays для dev/stage/prod;
- окремі теги образів і pipeline для кожного середовища.

**Коротко:**

- Образ бажано тримати максимально однаковим між середовищами.
- Різницю виносити в конфіг, а не в код/бінарник.
- Потрібен чіткий promotion flow (dev -> stage -> prod).

</details>

<details>
<summary>111. Як зменшити час збірки Docker Image?</summary>

#### Docker

Основні техніки:

1. Оптимізувати порядок layer-ів для cache hit.
2. Мінімізувати build context через `.dockerignore`.
3. Використовувати multi-stage і кеш залежностей.
4. Застосовувати BuildKit (`DOCKER_BUILDKIT=1`).
5. Використовувати remote/cache-from у CI.

**Коротко:**

- Найбільше впливає cache strategy.
- Менший context = швидший build.
- BuildKit значно покращує продуктивність збірки.

</details>

<details>
<summary>112. Як оновити контейнер без втрати даних?</summary>

#### Docker

Оновлення роблять через новий image і перевипуск контейнера, а стан зберігають
у volume/зовнішньому сховищі.

Патерн:

1. Зупинити старий контейнер.
2. Запустити новий контейнер з тим самим volume.
3. Переключити трафік.

**Коротко:**

- Дані мають бути винесені з контейнера.
- Оновлюється контейнер, а не mutable "ремонт" всередині нього.
- Для безперервності потрібен rolling/blue-green підхід.

</details>

<details>
<summary>113. Як мігрувати контейнер на інший сервер?</summary>

#### Docker

Зазвичай переносять не "живий контейнер", а артефакти:

- image (через registry або `save/load`);
- дані (volume backup/restore, DB replication, snapshots);
- конфіг/секрети/мережеві налаштування.

Після цього контейнер відтворюють на новому хості.

**Коротко:**

- Міграція = відтворення на новому хості, а не копіювання runtime стану.
- Ключові елементи: image + data + config.
- Потрібен план downtime або live-migration на рівні сервісу.

</details>

<details>
<summary>114. Як відлагодити проблему, якщо контейнер падає після запуску?</summary>

#### Docker

Чеклист:

1. `docker ps -a` — статус і exit code.
2. `docker logs <container>` — причина падіння.
3. `docker inspect` — env, command, mounts, healthcheck.
4. Перевірити ресурси (OOM, ліміти), порти, залежності.
5. Локально відтворити запуск із debug-командою.

**Коротко:**

- Починати з `ps -a` і `logs`.
- Найчастіші причини: неправильний CMD/ENTRYPOINT, конфіг, залежності.
- `inspect` дає повну технічну картину запуску.

</details>

<details>
<summary>115. Скільки контейнерів можна запустити на одному хості і від чого це залежить?</summary>

#### Docker

Фіксованого числа немає. Ліміт залежить від:

- CPU, RAM, disk I/O, мережі;
- профілю навантаження контейнерів;
- заданих лімітів ресурсів;
- overhead логування, моніторингу, runtime.

Практично визначають через навантажувальні тести і SLO.

**Коротко:**

- Кількість контейнерів визначається ресурсами і workload, а не Docker-правилом.
- Без лімітів контейнери можуть заважати один одному.
- Capacity planning обов'язковий для production.

</details>

<details>
<summary>116. Як організувати логування для контейнерів у production?</summary>

#### Docker

Рекомендації:

- писати логи в stdout/stderr;
- використовувати централізований збір (Fluent Bit/Vector/Logstash);
- зберігати structured logs (JSON);
- налаштувати ротацію і retention policy;
- корелювати логи з trace/request ID.

**Коротко:**

- Контейнерні логи не повинні жити лише локально на хості.
- Потрібна централізація, пошук і алертинг.
- Формат логів має бути машинно-оброблюваним.

</details>

<details>
<summary>117. Як організувати централізований моніторинг Docker?</summary>

#### Docker

Базовий підхід:

1. Метрики контейнерів і хостів (Prometheus/cAdvisor/node exporter).
2. Дашборди (Grafana).
3. Алертинг (Alertmanager, on-call маршрути).
4. Логи й трейси в єдиній observability-платформі.

**Коротко:**

- Моніторинг має бути централізованим і проактивним.
- Потрібні метрики, логи, алерти і чіткі runbooks.
- Без on-call процесу метрики мало корисні.

</details>

<details>
<summary>118. Як забезпечити високу доступність контейнерного застосунку?</summary>

#### Docker

Ключові практики:

- запускати кілька реплік сервісу;
- розносити репліки по різних вузлах/зонах;
- використовувати healthchecks і авто-відновлення;
- мати зовнішній load balancer;
- уникати single points of failure (БД, storage, ingress).

**Коротко:**

- HA = реплікація + автоматичне відновлення + балансування.
- Станові компоненти потребують окремої HA-стратегії.
- Регулярно тестуйте failover-сценарії.

</details>

<details>
<summary>119. Як працює service discovery у Swarm?</summary>

#### Docker

Swarm надає вбудований DNS для сервісів. Кожен сервіс отримує DNS-ім'я в
overlay-мережі.

Залежно від режиму endpoint (`VIP` або `dnsrr`) запити йдуть через virtual IP
або отримують список IP тасків.

**Коротко:**

- Service discovery у Swarm вбудований з коробки.
- Сервіси знаходять один одного по service name.
- `VIP`/`dnsrr` визначають модель маршрутизації.

</details>

<details>
<summary>120. У яких випадках не варто використовувати Docker?</summary>

#### Docker

Docker може бути не найкращим вибором, якщо:

- застосунок тісно залежить від специфіки ОС/ядра, несумісної з контейнерним
  підходом;
- критичні ultra-low-latency/real-time сценарії, де навіть невеликий overhead
  неприйнятний;
- команда не має операційної зрілості для підтримки контейнерної платформи;
- простий моноліт на одному сервері не потребує додаткової складності.

**Коротко:**

- Docker не самоціль, а інструмент.
- Якщо складність переважає вигоду, краще простіший підхід.
- Рішення має базуватись на вимогах системи і зрілості команди.

</details>
