# RGB-светодиод

### Описание

RGB-светодиод - это три светодиода (Красный, Зеленый, Синий) в одном корпусе с одним общим выводом (катодом (-) или анодом (+)).

Комбинируя яркость этих трех цветов, можно получить практически любой цвет. Белый свет — это максимум всех трех компонентов.

<figure><img src="../../.gitbook/assets/image (48).png" alt="" width="185"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (49).png" alt="" width="117"><figcaption></figcaption></figure>

Чтобы не плодить лишние выводы, все аноды или катоды светодиодов объединяются и получается 4 контакта: `R`, `G`, `B` и общий `COM`. Общим может быть как минус (катод) - _Common Cathode_, так и плюс (анод) - _Common Anode_:

<figure><img src="../../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>

Также на этой картинке показана распиновка типичного RGB светодиода: **самая длинная нога - общий вывод**, крайняя рядом с ней - красный, с другой стороны зелёный дальняя крайняя - синий.

### Схема подключения&#x20;

Если используем "голый" светодиод без резисторов:

<figure><img src="../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

**Важно!** Если хотим управлять оттенками, подключаем в ШИМ-пинам (обозначены \~)

Если используете модуль с резисторами, обратите внимание на подписи ножек и подключите в соответствии с надписями на плате.

### Программирование

#### Управление напрямую

Пишем программу, как будто для 3х светодиодов. В начале кода - `define` для зеленого, красного и синего;

В функции `setup()` - пишем `pinMode()` для всех трех:

```arduino
#define red 11
#define green 10
#define blue 9

void setup() {
  pinMode(red, OUTPUT);
  pinMode(green, OUTPUT);
  pinMode(blue, OUTPUT);
}
```

Для управления есть несколько вариантов. Если мы хотим получить r, g, b или их смеси, то используем простой способ. Просто включаем светодиоды по отдельности, чтобы получить нужный цвет:

<pre class="language-arduino"><code class="lang-arduino"><strong>// красный цвет
</strong><strong>digitalWrite(red,1);
</strong>digitalWrite(green, 0);
digitalWrite(blue, 0);
</code></pre>

<pre class="language-arduino"><code class="lang-arduino"><strong>// фиолетовый цвет
</strong><strong>digitalWrite(red,1);
</strong>digitalWrite(green, 0);
digitalWrite(blue, 1);
</code></pre>

Если светодиод подключен к ШИМ-выходам, то вместо 0/1 можно подавать на цвета значения от 0 (нет цвета) до 255 (макс. яркость), чтобы получить больше оттенков.

**НО** используем не команду `digitalWrite()`, а команду `analogWrite()`:

```arduino
analogWrite(red,245);
analogWrite(green, 73);
analogWrite(blue, 39);
```

С помощью кода выше включается вот такой цвет:

<figure><img src="../../.gitbook/assets/image (46).png" alt="" width="70"><figcaption></figcaption></figure>

Помните, что цвет на светодиоде и на экране компьютера будет отличаться! Значения RGB для любого цвета можно подобрать, например, тут: [https://htmlcolorcodes.com](https://htmlcolorcodes.com/)

#### Управление через библиотеку RGBLED

Еще один способ - использовать готовую библиотеку, например RGBLED от AlexGyver (документация тут [https://github.com/GyverLibs/RGBLED/tree/main](https://github.com/GyverLibs/RGBLED/tree/main))

Код получится короче:

```arduino
#include <RGBLED.h>
RGBLED rgb(11, 10, 9); // указываем пины по порядку red, green, blue

void setup() {
}

void loop(){
  rgb.setRGB(123, 0, 12); // задаем цвет по значениям RGB
  rgb.setColor(RGB::Color::Blue); // другой вариант - по названию цвета
  rgb.setRainbow(50); // другой вариант - по цветовому кругу от 0 до 255
}
```

### Задания для самостоятельного выполнения

Напишите код, который показывает на светодиоде 3 цвета по очереди (каждый цвет - 1 сек)
