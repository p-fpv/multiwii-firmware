# multiwii-firmware
Последний мой мод multiwii.  
Всё вместе: [github](https://github.com/p-fpv/multiwii-firmware/tree/upstream_shared/MW), [Гугл диск](https://drive.google.com/file/d/1GlJO6Vu7A0HQmhkHXaApKbCzUglgRTow/view?usp=sharing)  
MultiWii 2.4 MOD  
MultiWiiConf 2.4  
I2C_GPS_NAV_v2_2 fix  
MWOSD R1.6 mod(вход в меню как в inav,betaflight)  
WinGUI_2.3pre10b71

Только мод прошивка: [Гугл диск](https://drive.google.com/file/d/17jfpCTy4ixYAZFBwaKcJDYWvWd92Ipt0/view?usp=sharing)  
Только конфигуратор(нужна джава): [Гугл диск](https://drive.google.com/file/d/1jbhSE-_RR2zxRSAbHpM4CgAFXoieWKLG/view)
Только конфигуратор(джава встроена): [Гугл диск](https://drive.google.com/file/d/1mB_lhXBDC7ZyMOtupeILERtVu3wTjpcT/view)


Последняя прошивка multiwii mod, которая летала: [Гугл диск](https://drive.google.com/file/d/1JH-_mKMphsRR4L9IaIQ-quKSuu7EBwS5/view)  

Оригинал прошивки:
https://github.com/multiwii/multiwii-firmware  
Оригинал i2c-gps-nav (не компилируется в новых arduino ide): [Гугл](https://code.google.com/archive/p/i2c-gps-nav/downloads)

Схемы: [github](https://github.com/p-fpv/multiwii-firmware/tree/upstream_shared/MW/)  
Схема 1:[Гугл диск](https://drive.google.com/file/d/17C_0z1Cdw0nRtGb8KEJgoP1HGSZGw0Us/view?usp=sharing) Собирать по этой схеме, с остальным мои полномочия всё.  
Схема 2:[Гугл диск](https://drive.google.com/file/d/1oj_qtzbZ4pDPDSm9rZUpJZpI_0x48zMV/view?usp=sharing)  
Схема 3:[Гугл диск](https://drive.google.com/file/d/1BLuNCajbMPzegtK8vbNYMheQCvbtSR_r/view?usp=sharing)  

YouTube:
https://www.youtube.com/watch?v=mX8ljljpYV0


## Добавлено в прошивку:  
ap_mode - не надо щёлкать gps hold, чтобы поменять точку удержания.

LOW_THR_CONTROL - моторы управляются теперь и при нулевом газе, управление становится совсем вялое, но зато остаётся. Не стоит использовать с арм/дизарм со стиков!

disarm_without_thr - выключение моторов без необходимости ставить газ в ноль.

FS_RTH - возврат домой при фейлсейфе и автопосадка, а не просто падение.

Если включен land вместе с gps home, то автопосадка активируется после возврата домой.

motorsREV - микс под обратное вращение моторов, как на современных прошивках. Не проверялось, только для quadx.

motormap11on5 (микс)- Пин 5 повторяет выход мотора на 11 пине. Только для quadx. Делалось для прошивки Arduino4w-if в BLHeliSuite, чтобы в одной прошивке сразу были видны все регули.(пины 5 и 6 не работают при подключении каналов по отдельным проводам, тк это уже будут выходы под моторы).

При возврате домой начинает набирать высоту немного выше(на 2м), чем указано, но всё равно должен прекратить набор при превышении высоты установленной в конфиге. Делал это, чтобы не притормаживал при подлёте к заданной высоте, иначе мой коптер слишком долго прицеливался на минимально нужную высоту, решение так себе.

Теперь нет ошибки при компиляции в новом ide при выбранном UBLOX, не факт, что будет работать стабильно, но у меня за время тестов было всё нормально.

Фикс в для дисплея(ssd1106).

Убрал залипание режима baro при потере связи с gps модулем (обрыве проводов, иногда при сбое самого модуля), починил gps_fix при потере связи с gps модулем, теперь при обрыве проводов gps будет сброс режимов gps home и gps hold, а при включенном fs_rth сработает обычный fs, а не полёт в небо.

Не работал gps при выключении поддержки конфигуратора(msp телеметрии).

Поддержка QMC5883, вроде работает.

GPS_numSatARM, минимальное количество спутников для запуска, не ставить меньше 5.

## Полезные ссылки(без веб архива,  сайт может не работать)
https://web.archive.org/web/20160404165509/http://www.multiwii.com/wiki/index.php?title=Config.h в самом низу про кастомную ориентацию платы.  
https://web.archive.org/web/20191030042215/http://www.multiwii.com/wiki/index.php?title=Configuration  
https://web.archive.org/web/20160403031746/http://www.multiwii.com/wiki/index.php?title=PID  
https://web.archive.org/web/20180829201025/http://www.multiwii.com/wiki/index.php?title=Altitude_PID  
https://web.archive.org/web/20160424230204/http://www.multiwii.com/wiki/index.php?title=Pos_PI_controller  
https://web.archive.org/web/20160424230019/http://www.multiwii.com/wiki/index.php?title=Pos_Rate_PID_controller (в gps hold почему-то расстояние действия больше, чем GPS_WP_RADIUS, мб был виноват I2C_GPS_NAV)  
https://web.archive.org/web/20160424230158/http://www.multiwii.com/wiki/index.php?title=Nav_Rate_PID_controller  
https://web.archive.org/web/20191229102216/http://www.multiwii.com/wiki/index.php?title=Flightmodes  
https://www.magnetic-declination.com/ магнитное склонение   
http://www.multiwii.com/forum/viewtopic.php?t=3578 TPA  
