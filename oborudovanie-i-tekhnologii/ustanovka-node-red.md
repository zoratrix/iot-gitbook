# Установка Node-red

Есть два способа установки Node-red. Попробуйте первый, если не выйдет, попробуйте второй

## Установка Node-red (способ 1, прямая, <500 мб)

1\) Скачайте и установите Node.js (кнопка Get Node.js, затем кнопка Windows installer): [https://nodejs.org/en/](https://nodejs.org/en/). При установке согласитесь со всем предлагаемым, в т.ч. нажмите галочку "install necessary tools":

<figure><img src="../.gitbook/assets/image (247).png" alt=""><figcaption></figcaption></figure>

После основной части установки появится окно PowerShell, в котором установится несколько пакетов. Дождитесь, пока это окно пропадет (либо там будет написано, что все установлено, либо там несколько раз подряд будет появляться одна и та же строчка с ошибкой)

2\) Откройте командную строку. Напишите и выполните команду:

```
node --version && npm --version
```

Это проверка установки node js. Если все ок, то увидите что-то типа:

```
v18.15.0
9.5.0
```

3\) Установка Node-red. Для этого в командной строке выполните команду:

```
npm install -g --unsafe-perm node-red
```

4\) готово. Теперь вы можете запустить node-red как в "Смене" (откройте командную строку и выполните node-red или нажмите на пуск, напишите node-red и нажмите enter)

5\) зайдите в веб-интерфейс. Для этого откройте браузер и запустите localhost:1880

6\) устанавливаем библиотеки. В веб-интерфейсе откройте меню в правом верхнем углу, выберите "управление палитрой"

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Выберите вкладку "установить". В поле для ввода вставьте название пакета (список будет ниже), затем нажмите install у появившегося в поиске варианта:

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Список нужных пакетов:**

* @flowfuse/node-red-dashboard&#x20;
* node-red-contrib-iot-controlcenter

Готово, вы установили нод ред и вы прекрасны!

## Установка Node-red (способ 2, на виртуальную машину, 8 гб)

1\) Скачайте файл (образ системы **с уже установленным node-red и библиотеками**) [https://drive.google.com/file/d/1AfVdII33FMgfsmDHc1MqGLo\_tSIbCCd5/view?usp=drive\_link](https://drive.google.com/file/d/1AfVdII33FMgfsmDHc1MqGLo_tSIbCCd5/view?usp=drive_link)

2\) Скачайте и установите Virtual Box [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) (в левой части экрана ссылка Windows hosts)

3\) Откройте Virtual Box. В интерфейсе нажмите кнопку Import:

<figure><img src="../.gitbook/assets/image (246).png" alt=""><figcaption></figcaption></figure>

4\) В открывшемся окне выберите файл .ova скачанный в пункте 1

<figure><img src="../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

5\) Далее при необходимости вы можете поменять место хранения файлов виртуальной машины (если у вас нет проблем с местом на диске C, то ничего не меняйте)

<figure><img src="../.gitbook/assets/image (4) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

6\) Дождитесь окончания импорта

<figure><img src="../.gitbook/assets/image (5) (1) (1).png" alt=""><figcaption></figcaption></figure>

7\) после окончания загрузки не запускайте виртуальную машину и сначала настройте сеть. нажмите "настройки":

<figure><img src="../.gitbook/assets/image (248).png" alt=""><figcaption></figcaption></figure>

раздел "сеть":

<figure><img src="../.gitbook/assets/image (249).png" alt=""><figcaption></figcaption></figure>

тип подключения должен быть "сетевой мост", имя - скорее всего у вас там так же будет realtek..., то есть оставьте по умолчанию

8\) закройте настройки, вернитесь к основной странице virtual box. выберите виртуальную машину в списке слева и нажмите "запустить"

<figure><img src="../.gitbook/assets/image (250).png" alt=""><figcaption></figcaption></figure>

Дождитесь загрузки. В открывшемся окне виртуальной машине у вас появится требование ввести логин.&#x20;

* login: redadmin
* password: 12345

Ввкдите логин и нажмите энтер:

<figure><img src="../.gitbook/assets/image (251).png" alt=""><figcaption></figcaption></figure>

Далее введите пароль. ВНИМАНИЕ - при вводе пароля символы не отображаются. Просто введите 12345 и нажмите энтер. Если вы все ввели верно, у вас загрузится система и появится терминал

<figure><img src="../.gitbook/assets/image (252).png" alt=""><figcaption></figcaption></figure>

На этом все, сверните виртуальную машину и можно идти работать. Единственное, при первом запуске вам нужно узнать ip виртуальной машины для подключения. Для этого в терминале виртуальной машины введите команду `ifconfig` и нажмите энтер:

<figure><img src="../.gitbook/assets/image (253).png" alt=""><figcaption></figcaption></figure>

Просто запомните или запишите это ip и используйте его.

Чтобы открыть веб-интерфейс нод ред, сверните виртуальную машину, откройте бразуер и введите в адресную строку вместо `localhost:1880` (как в смене) `ip-адрес:1880`, например `192.168.0.15:1880`, вот так:

<figure><img src="../.gitbook/assets/image (254).png" alt=""><figcaption></figcaption></figure>

**ВАЖНО:** для входа в нод ред используйте логин `admin` пароль `12345`

<figure><img src="../.gitbook/assets/image (255).png" alt=""><figcaption></figcaption></figure>
