# Linux kernel 3.18.120 for BQS-5020
Это исходный код ядра линукс для портирования дистрибутивов линукс для BQS-5020

Работа ядра тестировалось на 3 ревизии. Проверялось ядро на дистрибутиве RPIOS Debian 12 Bookworm

### Что работает/неработает:
 + [x] 3D
 + [x] Экран(fbdev, fbcon не работает)
 + [x] Акселерометр(BMA222)
 + [ ] Аудио
 + [ ] Блютуз
 + [ ] Вайфай
 + [ ] Модем
 + [x] Вибромотор
 + [x] Светодиоды
 + [ ] Микрофон
 + [ ] Камеры
 + [x] Вспышка
 + [x] Батарея
 + [x] Сон(частично)
 + [x] Тачскрин	
## Сборка ядра
Установка пакетов для сборки
```
sudo apt install -y python2 git fakeroot build-essential ncurses-dev xz-utils libssl-dev bc flex libelf-dev bison
```

Линкуем /usr/bin/python2 >>> /usr/bin/python
```
ln -s /usr/bin/python2 /usr/bin/python
```

Скачиваем тулчейн(в ~ директории):
```
cd ~
git clone https://github.com/LineageOS/android_prebuilts_gcc_linux-x86_arm_arm-linux-androideabi-4.9.git -b cm-14.1
```
Сборка ядра:
```
cd kernel_bqs5020
mkdir out
make O=out ARCH=arm CROSS_COMPILE=/home/mg30/android_prebuilts_gcc_linux-x86_arm_arm-linux-androideabi-4.9/bin/arm-linux-androideabi- V3702_defconfig # ВАЖНО! Заменить mg30 на текущего пользователя!
make O=out ARCH=arm CROSS_COMPILE=/home/mg30/android_prebuilts_gcc_linux-x86_arm_arm-linux-androideabi-4.9/bin/arm-linux-androideabi- -j8 # ВАЖНО! Заменить mg30 на текущего пользователя!
```

Скомпилированное ядро хранится в out/arch/arm/boot/zImage-dtb
