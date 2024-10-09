# BIOS_X99_China_Optimize
***[DISCORD](https://discord.com/invite/EJRjXXtjMV)***

Гайд находится в статусе написания поэтому могут быть ошибки, недосказанности и много всякой не хорошей уйни.
## Предупреждение
ВАЖНО ПОНИМАТЬ ЧТО ЛЮБЫЕ МАХИНАЦИИ С ПРОШИВКОЙ БИОСА ПРИ ИЗМЕНЁННЫХ НАСТРОЙКАХ(ОСОБЕННО ТЕХ ЧТО НАХОДЯТСЯ В ТЕСТЕ) ДЕЛАЮТСЯ НА СВОЙ СТРАХ И РИСК. ГАЙД НЕ МОЖЕТ ЯВЛЯТЬСЯ 100% РЕШЕНИЕМ ИБО БИОСЫ У ВСЕХ РАЗНОЙ СТЕПЕНИ ГОВЁНОСТИ И ЧТО МОЖЕТ НОРМАЛЬНО РАБОТАТЬ НА ОДНОЙ ПЛАТЕ МОЖЕТ СПОКОЙНО НЕ РАБОТАТЬ НА ДРУГОЙ. На большинстве Huananzhi и Machinist всё должно работать, но кто знает что может выстрелить.

Для отката биоса в случае проблем нужен программатор CH341A.

Гайд основан на:
1. [Биосы кошака/там же и некоторые гайды](https://github.com/Koshak1013/HuananzhiX99_BIOS_mods/tree/master)
2. [Xeon-e5450.ru faq](https://xeon-e5450.ru/socket-2011-3/faq/)
3. [Драйвера для x99](https://xeon-e5450.ru/socket-2011-3/drivers-x99/)
4. [Хак турбобуста](https://xeon-e5450.ru/socket-2011-3/e5-2600-v3/dobavlyaem-anlok-v-bios-raz-i-navsegda-cherez-s3turbotool/)
5. [GENERAL Overclock.Net BIOS](https://www.overclock.net/threads/gaming-and-mouse-response-bios-optimization-guide-for-modern-pc-hardware.1433882)
6. [INTEL BIOS SETTINGS EXPLANATION](https://docs.google.com/document/d/1s43_3YGJIy3zs0ZIksoOmxgrDKnu4ZNhhnXW_NiJZ0I/edit)
7. [Hidden bios settings list - Des1de & CatGamerOP](https://docs.google.com/document/d/1KIW7D9tCcv5sBBCh9qR6S-jZSsvTKQFwtOfBhkaBD4E/edit)
8. [Intel Hidden Bios Setting Guide Scewin By Ancel](https://docs.google.com/document/d/1ztCWHU2vCG9hnD_94VhlnsLJq1-0Mq7OwhjF79JsYgA/edit)
9. Свои методы реализации некоторых моментов при настройке.
10. [S3TurboTool](https://4pda.to/forum/index.php?showtopic=1015953)
11. [Overclockers 2011-3](https://forums.overclockers.ru/viewtopic.php?f=1&t=602922&start=520)
12. [Разгон ОЗУ x99 Overclockers](https://forums.overclockers.ru/viewtopic.php?f=4&t=622568)

## 1. Подбор биоса для своей материнской платы
Заходим по первой [ссылке](https://github.com/Koshak1013/HuananzhiX99_BIOS_mods/tree/master) на гитхаб кошака и ищем свою материнскую плату. Если твоей платы там нет, то можно перейти в ТГ который указан в там же, предоставить дамп оригинадьного биоса и попросить разлочить в нём настройки таймингов(если таковых не имеется в стоковом биосе). 

Можно столкнуться с тем что у платы несколько ревизий и биос от одной может не подойти к другой. Как в этом примере:
![](https://github.com/DmitryPonyn/BIOS_X99_China_Optimize/blob/main/images/BIOS_rev.png)

В таком случае нужно осмотреть материнскую плату на наличее надписей Ver/Rev и исходя из неё выбрать нужную версию биоса. Если надписи такой нет, то нужно зайти на [xeon-e5450.ru](xeon-e5450.ru) и в выпадающем списке вверху "2011-3" выбрать свою материнскую плату и там будет как различить разные ревизии.

После нахождения нужной папки скачиваем zip архив в названии которого есть приписка kot и разорхивируем в корень диска C в папку BIOS.

Для того чтобы удостовериться что мы скачали верный биос скачиваем S3TurboTool по 10 [ссылке](https://4pda.to/forum/index.php?showtopic=1015953) и распаковываем архив в папку в которую распаковали наш биос. Запускаем S3TurboTool из папки в которую мы его распаковали, соглашаемся с соглашением и делаем бекап нынешнего биоса в папку с программой в формате .bin. Далее в том же окне S3TurboTool открываем два окна AMIBCP в которых открываем бекап нынешнего биоса и который мы скачали с гитхаба. В обоих окнах выбераем вверху вкладку DMI Tables и там пункт "Base Board (or Module) Information (Type 2)" и сравниваем информацию в строках которые выдаст программа.
![](https://github.com/DmitryPonyn/BIOS_X99_China_Optimize/blob/main/images/BIOS_check.png)

Если всё сошлось то прекрасно, значит мы скачали то что нужно.

## 2. Разгон/анлок турбобуста(если процессор v4 пропускай) 

<details>
<summary>Разгон 16xx v3</summary>

ДАННЫЙ МЕТОД РАБОТАЕТ ТОЛЬКО ЕСЛИ В ТВОЕЙ МАТЕРИНСКОЙ ПЛАТЕ СТОИТ СЕРВЕРНЫЙ ЧИПСЕТ, ЕСЛИ У ТЕБЯ ДЕСКТОПНЫЙ, ТО ТВОЙ ЕДИНСТВЕННЫЙ ВАРИАНТ ЭТО АНЛОК ТУРБОБУСТА. 

1. Открываем S3TurboTool. 
2. Нажимаем "Прошить BIOS" и выбераем тот биос который мы скачали, после чего начинаем прошивку. 
3. По её завершении выключаем ПК и сбрасываем биос перемычкой или батарейкой. 
4. Включаем комп и заходим в BIOS. 
5. Идём по пути IntelRCSetup>OverClocking Feature. 
6. Изменяем OverClocking Feature с Disabled на Enabled. 
7. Открываем появившийся пункт Processor. 
8. Тут мы будем изменять значение "Core Max OC Ratio" и можно начать с значения 40.

Логика этого пункта проста. Число которое мы в нём ставим является множителем на который умножается шина и получается частота процессора. Тоесть 40*100=4000mhz=4Ghz. 

9. Так же будем изменять значение "Core Extra Turbo Voltage", можно начать со значения 1200.

Значение этой настройки указывает напряжение в милливольтах. Таким образом 1200 = 1.2 вольта. Поднимать выше 1300-1350 не стоит, но если хочется добиться диких результатов, то можно и поднять. 

10. Сохраняем настройки, загружаемся в винду и запускаем стресстест OCCT. 
Пресет настроек для теста:

    - Вкладка: CPU
    - Набор данных: Большой
    - Режим: Тяжёлый
    - Нагрузка: Переменная
    - Инструкции: SSE (не AVX)
    - Потоки: Авто 

Если тест за ≈10 минут не вылетел в синий экран, то можно вернуться к 5 пункту и повышать множитель дальше. Если же тест вылетел синим экраном, то нужно повысить напряжение. Лучше повышать шагами по 50. Тоесть 1250,1300,1350 и тд. 

Когда решил что уже установил достаточный множитель и гнать дальше не будешь, проведи тот же стресс тест, но уже час. 
</details>

<details>
<summary>Анлок турбобуста 26xx v3</summary>

1. Запускаем S3TurboTool и нажимаем MMTool5
2. В появившейся утилите "MMTool Aptio" нажимаем "Load Image" и выбираем биос, в который будем добавлять драйвер анлока
3. Переходим на вкладку "CPU Patch", выделяем микрокод "6F 06F2", отмечаем "Delete a Patch Data", нажимаем Apply и соглашаемся
4. Нажимаем "Save Image" и закрываем "MMTool Aptio"
5. В S3TurboTool нажимаем AMIBCP
6. В появившейся утилите AMIBCP открываем биос
7. Раскрываем список и идём по пути "Common RefCode Configuration > IntelRCSetup > Advanced Power Management Configuration > CPU C State Control" (путь может отличаться на брендовых материнских платах)
8. Справа, в столбце Optimal, двойным кликом меняем значение параметров:
    * "Package C State limit" на "C2 state"
    * "CPU C3 report" на "Enable"
    * "CPU C6 report" на "Disable"
9. Закрываем окно AMIBCP и соглашаемся на сохранение внесённых изменений.

Далее надо определиться с тем, хотим ли мы найти максимальное значение андервольта или нет.

<details>
<summary>Если не хотим</summary>

1. В S3TurboTool нажимаем "Собрать драйвер"
2. Выбераем тип драйвера PEI.
3. Ставим галочку на "Смещение напряжения" и выставляем -40 Core и -40 Cache. Снимаем галочку с пункта "Код биппера в драйвер" и нажимаем "Собрать драйвер".
4. В S3TurboTool нажимаем UEFITool
5. В появившейся утилите UEFITool открываем биос
6. Раскрываем список и идём по пути "Intel image > BIOS region > 8C8CE578-...(самый нижний, в котором PEI драйверы) >"
7. Находим 271DD6F2-... (модуль PchS3Peim)
8. Правый клик по нему, нажимаем "Replace as is...", выбираем собранный ранее драйвер (находится в папке S3TurboHack).
9. Прошиваем биос и наслаждаемся.
</details>


<details>
<summary>Если хотим</summary>

1. Скачиваем [Rufus](https://github.com/DmitryPonyn/BIOS_X99_China_Optimize/raw/refs/heads/main/software/rufus-4.5p.exe) и записываем флешку с такими параметрами:

![](https://github.com/DmitryPonyn/BIOS_X99_China_Optimize/blob/main/images/rufus.png)

2. Скачиваем [Unlock.zip](https://github.com/DmitryPonyn/BIOS_X99_China_Optimize/raw/refs/heads/main/software/Unlock.zip) и распаковываем в любую папку.
3. Открываем файл v3_payne.asm через блокнот и начинаем проверять значения андервольта на ядро.
4. Для этого изменяем строчку "CoreVOffset" с -0 на -100.
5. Запускаем батник !compile.cmd после чего у нас создастся файл 1.efi.
6. Скачиваем [USB.zip](https://github.com/DmitryPonyn/BIOS_X99_China_Optimize/raw/refs/heads/main/software/USB.zip) и распаковываем на флешку.
7. Файл 1.efi переносим в корень той же флешки.
8. Прошиваем наш модифицированный биос.
9. Перезагружаемся и попадаем в биос через который запускаемся с флешки.
10. После того, как загрузится оболочка, появится сообщение "Press ESC in 5 seconds to skip startup.nsh or any other key to continue". Нажимаем ESC.
11. Смотрим на Mapping Table и определяем, как смонтировалась наша флешка и диск, на котором установлена ОС. На скриншоте видно, что в данном случае, флешка смонтировалась как FS0, а диск как FS1. Чтобы избежать путаницы можно временно отключить все не системные накопители.

![](https://github.com/DmitryPonyn/BIOS_X99_China_Optimize/blob/main/images/mapping-table.jpg)

12. Мы можем протестировать 1.EFI командой load fs0:\1.EFI. Если система не повисла или не перезагрузилась, то пишем Exit и загружаемся в винду через пункт в биосе. Если при загрузке системы с 1.efi она вылетела в синий экран или произошло что-то из перечисленного ранее, то перезагружаем комп, возвращаемся к пункту 4, но теперь -100 убавляем по 5. Т.е. -95, -90 и тд.
13. После удачной загрузки в систему прогоняем часовой тест в OCCT с такими параметрами:

    - Вкладка: CPU
    - Набор данных: Большой
    - Режим: Тяжёлый
    - Нагрузка: Переменная
    - Инструкции: SSE (не AVX)
    - Потоки: Авто

14. Если система прошла тест, то можно приступать к офсету напряжения на кэш. Для этого меняем строчку "CacheVOffset" с -0 на -100 и проделываем всё тоже самое что с андервольтом ядер.
15. При андервольте кэша проводим 10 минутный стресс тест в LinX:
    - Память: 8192МБ

Когда система станет стабильно проходить тесты можно протестить офсеты в твоих задачах для большей уверенности в их стабильности. 

Для прошивки биоса с нужным офсетом:
1. В S3TurboTool нажимаем "Собрать драйвер"
2. Выбераем тип драйвера PEI.
3. Ставим галочку на "Смещение напряжения" и выставляем число которое вышло при подборе андервольтинга на ядро и кэш. Снимаем галочку с пункта "Код биппера в драйвер" ставим галочку у пункта "Включить баг SVID/FIVR" и нажимаем "Собрать драйвер".
4. В S3TurboTool нажимаем UEFITool
5. В появившейся утилите UEFITool открываем биос
6. Раскрываем список и идём по пути "Intel image > BIOS region > 8C8CE578-...(самый нижний, в котором PEI драйверы) >"
7. Находим 271DD6F2-... (модуль PchS3Peim)
8. Правый клик по нему, нажимаем "Replace as is...", выбираем собранный ранее драйвер (находится в папке S3TurboHack).
9. Прошиваем биос и наслаждаемся.
</details>


</details>

## 2.2 Как и когда использовать баг FIVR. (Если проц v4, то пропускай)
Начнём с того что это вообще за такой баг. Баг SVID/FIVR это так называемый vcc1.8 в других драйверах, при определённых значениях SVID/FIVR сносит крышу и так как потребление определяется с ошибкой в меньшую сторону слетает ограничение TDP.

Лично я советую использовать его если у нас уже имеются максимальные значения для офсета чтобы процессор при баге потреблял меньше, а соответсвенно меньше грелся и грел врм. Спокойно использовать баг FIVR можно даже на слабенькой Atermiter D4 при условии что корпус продуваемый и обдувает зону VRM, а так же используется процессор до 2660v3(2643v3 и 2637v3 не в счёт). На платах подороже уже нужно смотреть сколько мегагерц нам не хватает до максимального буста, если ядер не много и не хватает 100-200мгц, то тоже можно попробовать протестить систему с багом. Для особо отчаяных кто захочет использовать баг на пару с 2696v3 важно понимать, что даже с андервольтом в 90mv на ядра и кэш, процессор сможет вытягивать за 200 ватт, а на такое потребление ни одна китайская материнка не предназначена.

Для создания драйвера с багом FIVR:
1. В S3TurboTool нажимаем "Собрать драйвер"
2. Выбераем тип драйвера PEI.
3. Ставим галочку на "Смещение напряжения" и выставляем число которое вышло при подборе андервольтинга на ядро и кэш. Снимаем галочку с пункта "Код биппера в драйвер" ставим галочку у пункта "Включить баг SVID/FIVR" и нажимаем "Собрать драйвер".
4. В S3TurboTool нажимаем UEFITool
5. В появившейся утилите UEFITool открываем биос
6. Раскрываем список и идём по пути "Intel image > BIOS region > 8C8CE578-...(самый нижний, в котором PEI драйверы) >"
7. Находим 271DD6F2-... (модуль PchS3Peim)
8. Правый клик по нему, нажимаем "Replace as is...", выбираем собранный ранее драйвер (находится в папке S3TurboHack).
9. Прошиваем биос и наслаждаемся.

## 3 Добавление поддержки ReBar
1. Скачиваем [ReBarDxe.ffs и ReBarState.exe](https://github.com/xCuri0/ReBarUEFI/releases/latest)
2. Открываем в [UEFITool 0.28.0](https://github.com/LongSoft/UEFITool/releases/tag/0.28.0) файл биоса
3. Раскрываем список и идём по пути "Intel image > BIOS region > 8C8CE578-...(предпоследний, второй снизу, в котором DXE драйверы) >"
4. Прокручиваем в самый низ и находим последний DXE драйвер в списке
5. Правый клик по нему, нажимаем "Insert after...", выбираем скачанный ранее файл ReBarDxe.ffs
6. Выбираем "File > Save image file...", сохраняем. Прошиваем.
7. Активируем настройку Above4GDecoding
8. Из под Windows запускаем ReBarState.exe и вводим две цифры "32" и нажимаем ввод. Перезагружаемся.
9. В GPU-Z можно проверить состояние ReBar, в т.ч. выполнение каждого условия для активации

## 4 Отключение бипера

***Старый метод, крайне редко работающий, поэтому что бипер действительно перестнет пищать гарантий не дам.***

1. Нам нужны определённые модули из биоса, чтобы их получить открываем S3TurboTool, нажимаем UEFITool и в появившейся утилите открываем биос.
2. Раскрываем список и идём по пути "Intel image > BIOS region > 8C8CE578-...(предпоследний, второй снизу, в котором DXE драйверы) >".
3. В самом правом столбце есть названия модулей, ищем Bds(ищите начиная сверху) и StatusCodeDxe(ищите начиная снизу).
4. Правый клик по "PE32 image section", нажимаем "Extract body...", сохраняем модуль с соответствующим названием, чтобы не запутаться. Также делаем и со вторым модулем.

![](https://github.com/Koshak1013/HuananzhiX99_BIOS_mods/raw/master/.git_images/screen03.png)

5. В S3TurboTool нажимаем Beep в верхнем правом углу.
6. Нажимаем левый значок для открытия файла модуля и выбираем один из модулей.
7. Нажимаем правый значок "Beep Off" и делаем то же самое со вторым модулем.
8. Теперь снова открываем UEFITool (повторяем шаги 1-3 инструкции), делаем правый клик по "PE32 image section", нажимаем "Replace body...", и выбираем соответствующий модуль. Также делаем и со вторым модулем.
9. Выбираем "File > Save image file...", сохраняем. Биос готов к прошивке. Прошить можно также соответствующей кнопкой в S3TurboTool.

*Если бипер по-прежнему издаёт звуки, то попробуйте также обработать модуль StatusCodePei (в разделе с PEI модулями).*
