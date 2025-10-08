---
hidden: true
icon: wallet
---

# Как подключить свой кошелёк к платформе Dojo.

Для того чтобы подключить свой кошелёк к платформе  Dojo вам понадобится браузерное расширение криптокошелька например  "Bittensor": &#x20;

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

или "Talisman":

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

\
Чтобы  подключить к платформе свой браузер через  криптокошелёк , вам нужно импортировать горячий ключ в свой  браузерный криптокошелёк. &#x20;

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

И затем  подключаться к платформе Dojo при помощи  этого горячего ключа.&#x20;

<figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

\
Обычно у вас в кошельке могут находиться  только холодные ключи. Но вы точно так же можете импортировать в него и ваши горячие ключи.\
\
<mark style="color:$success;">**Для этого вам понадобится сид-фраза от горячего ключа.**</mark>\
\
Чтобы создать горячий ключ и сид-фразу к нему вам понадобится `btcli` — интерфейс командной строки Bittensor.&#x20;

<figure><img src=".gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

<mark style="color:$warning;">О его установке и использовании подробно написано</mark> [<mark style="color:blue;">**здесь**</mark>](https://docs.learnbittensor.org/getting-started/install-btcli) <mark style="color:$warning;">в официальной документации Bittensor.</mark>\
\
Для работы с Dojo удобнее всего устанавливать и использовать `btcli`  локально на ваш ПК. Вам не нужно запускать отдельный VPS/VDS. Вы сможете выполнять работу в качестве  майнера или контрибутора локально на вашем ПК, без необходимости круглосуточного подключения к подсети Dojo. Вам нужно будет подключаться к  платформе Dojo только тогда когда вы будете работать и выполнять задания. &#x20;

<mark style="color:$success;">**Платформа это всё что вам нужно для работы с заданиями.**</mark>

<figure><img src=".gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

\
Ниже короткая пошаговая инструкция как вы можете создать и импортировать в свой кошелёк горячую клавишу:\


1.  &#x20;Установите  `btcli` — интерфейса командной строки Bittensor. О его установке и использовании подробно написано [здесь](https://docs.learnbittensor.org/getting-started/install-btcli) в официальной документации Bittensor:\
    `pip install bittensor-cli`

    \
    \
    \
    \

2.  Создайте новый холодный ключ (или используйте свой имеющийся холодный ключ):\
    `btcli wallet new-coldkey`ey\


    <figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>


3.  Создайте горячий ключ.\
    `btcli wallet new-hotkey`\


    <figure><img src=".gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>


4.  Сохраните сид-фразу горячего ключа:\


    <figure><img src=".gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>


5.  Импортируйте новый кошелек в браузерном кошельке при помощи сид-фразы горячего ключа.\


    <figure><img src=".gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>


6.  Подключитесь к платформе выбрав  ваш горячий ключ.\


    <figure><img src=".gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>


7.  После успешного подключения всё должно выглядеть вот таким образом и задачи должны  отображаться сразу же:\


    <figure><img src=".gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>
