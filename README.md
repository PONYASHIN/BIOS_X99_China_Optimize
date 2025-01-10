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

В таком случае нужно осмотреть материнскую плату на наличее надписей Ver/Rev и исходя из неё выбрать нужную версию биоса. Если надписи такой нет, то нужно зайти на [xeon-e5450.ru](https://xeon-e5450.ru) и в выпадающем списке вверху "2011-3" выбрать свою материнскую плату и там будет как различить разные ревизии.

После нахождения нужной папки скачиваем zip архив в названии которого есть приписка kot и разорхивируем в корень диска C в папку BIOS.

Для того чтобы удостовериться что мы скачали верный биос скачиваем S3TurboTool по 10 [ссылке](https://4pda.to/forum/index.php?showtopic=1015953) и распаковываем архив в папку в которую распаковали наш биос. Запускаем S3TurboTool из папки в которую мы его распаковали, соглашаемся с соглашением и делаем бекап нынешнего биоса в папку с программой в формате .bin. Далее в том же окне S3TurboTool открываем два окна AMIBCP в которых открываем бекап нынешнего биоса и который мы скачали с гитхаба. В обоих окнах выбераем вверху вкладку DMI Tables и там пункт "Base Board (or Module) Information (Type 2)" и сравниваем информацию в строках которые выдаст программа.
![](https://github.com/DmitryPonyn/BIOS_X99_China_Optimize/blob/main/images/BIOS_check.png)

Если всё сошлось то прекрасно, значит мы скачали то что нужно.

## 2. Разгон/анлок турбобуста(если процессор v4 пропускай) 

<details>
<summary>Разгон 16xx v3</summary>

ДАННЫЙ МЕТОД РАБОТАЕТ ТОЛЬКО ЕСЛИ В ТВОЕЙ МАТЕРИНСКОЙ ПЛАТЕ СТОИТ СЕРВЕРНЫЙ ЧИПСЕТ И ПРОЦЕССОР ИМЕЕТ РАЗБЛОКИРОВАННЫЙ МНОЖИТЕЛЬ, ЕСЛИ У ТЕБЯ МНОЖИТЕЛЬ ЗАБЛОКИРОВАН, ТО ТВОЙ ЕДИНСТВЕННЫЙ ВАРИАНТ ЭТО АНЛОК ТУРБОБУСТА. 

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

!!! Иногда для стабильности разгона можно попробовать снять ограничение по току разблокировав пункт меню Program PP0_CURT_CFG_CTRL_MSR. Для этого открываем наш дамп биоса через AMIBCP и идём по пути IntelRCSetup>Advanced Power Management Configuration>CPU - Advanced PM Tuning и там на против пункта Program PP0_CURT_CFG_CTRL_MSR в колонке Access/Use выставляем USER. После чего сохраняем наш дамп и прошиваем. Теперь в биосе по тому же пути (IntelRCSetup>Advanced Power Management Configuration>CPU - Advanced PM Tuning) заходим в разблокированный пункт Program PP0_CURT_CFG_CTRL_MSR и там выставляем настройку Current Config в положение Enable и значение Current Limitation выставляем по принципу: допустим лимит нужен 200А - значит ставим 1600. Проще говоря требуемый ток умножаем на 8 и вбиваем полученное значение. После этого разгон должен быть более стабильным.
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
3. Ставим галочку на "Смещение напряжения" и выставляем число которое вышло при подборе андервольтинга на ядро и кэш. Снимаем галочку с пункта "Код биппера в драйвер" и нажимаем "Собрать драйвер".
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

Лично я советую использовать его если у нас уже имеются максимальные значения для офсета чтобы процессор при баге потреблял меньше, а соответсвенно меньше грелся и грел врм. Спокойно использовать баг FIVR можно даже на слабенькой Atermiter D4 при условии что корпус продуваемый и обдувает зону VRM, а так же используется процессор до 2660v3(2643v3 и 2637v3 не в счёт). На платах подороже уже нужно смотреть сколько мегагерц нам не хватает до максимального буста, если ядер не много и не хватает 100-200мгц, то тоже можно попробовать протестить систему с багом. Для особо отчаяных кто захочет использовать баг на пару с 2696v3 важно понимать, что даже с андервольтом в 90mv на ядра и кэш, процессор сможет вытягивать за 200 ватт, а на такое потребление ни одна китайская материнка не предназначена. Для него чтобы получить максимальный буст в играх лучше использовать [отключение ядер](#71-ядра).

!!! Иногда выходит так что при использовании бага FIVR процессор может работать на более низком андервольте, что при использовании бага при котором слетает ограничение по питанию может ещё немного сократить потребление камня, а значит и нагрев VRM.

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

После перезапуска можно протестить частоту в нагрузке, она будет выше, но есть шанс упереться в лимит EDP (т.е по току), данный лимит обойти никак нельзя. Как пример, мой 2696v3 с офсетами (-70 -50) и багом fivr из-за этого может удерживать только 3.6ггц. Важно помнить что из-за слетевшего лимита TDP у нас перестанет правильно работать датчик потребления даже если до бага он работал исправно.

!!! На некоторых платах можно попробовать снять ограничение по току разблокировав пункт меню Program PP0_CURT_CFG_CTRL_MSR. Для этого открываем наш дамп биоса через AMIBCP и идём по пути IntelRCSetup>Advanced Power Management Configuration>CPU - Advanced PM Tuning и там на против пункта Program PP0_CURT_CFG_CTRL_MSR в колонке Access/Use выставляем USER. После чего сохраняем наш дамп и прошиваем. Теперь в биосе по тому же пути (IntelRCSetup>Advanced Power Management Configuration>CPU - Advanced PM Tuning) заходим в разблокированный пункт Program PP0_CURT_CFG_CTRL_MSR и там выставляем настройку Current Config в положение Enable и значение Current Limitation выставляем по принципу: допустим лимит нужен 200А - значит ставим 1600. Проще говоря требуемый ток умножаем на 8 и вбиваем полученное значение.

## 3. Добавление поддержки ReBar
1. Скачиваем [ReBarDxe.ffs и ReBarState.exe](https://github.com/xCuri0/ReBarUEFI/releases/latest)
2. Открываем в [UEFITool 0.28.0](https://github.com/LongSoft/UEFITool/releases/tag/0.28.0) файл биоса
3. Раскрываем список и идём по пути "Intel image > BIOS region > 8C8CE578-...(предпоследний, второй снизу, в котором DXE драйверы) >"
4. Прокручиваем в самый низ и находим последний DXE драйвер в списке
5. Правый клик по нему, нажимаем "Insert after...", выбираем скачанный ранее файл ReBarDxe.ffs
6. Выбираем "File > Save image file...", сохраняем. Прошиваем.
7. Активируем настройку Above4GDecoding
8. Из под Windows запускаем ReBarState.exe и вводим две цифры "32" и нажимаем ввод. Перезагружаемся.
9. В GPU-Z можно проверить состояние ReBar, в т.ч. выполнение каждого условия для активации

## 4. Отключение бипера

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

## 5. Настройка ОЗУ

Этот метод снижения таймингов взят [Отсюда](https://www.youtube.com/watch?v=2UdU4n6B0V8)
    
1. Выставляем частоту памяти в зависимости от процессора (2640v3 и ниже - 1867, всё что выше 2133, а если камень v4 то 2400. Если же мы используем ddr3, то можно попробовать погнать её до 2133, а в случае неудачи придётся использовать 1867).
2. "Command Timing" ставим на 1N.
3. Начинаем снижать тайминг "CAS Latency" до 14 и проводим тест памяти в [testmem5](https://github.com/DmitryPonyn/BIOS_X99_China_Optimize/raw/refs/heads/main/software/TM5.zip) с профилем Extreme1 @anta777 и ждём не менее 20 минут. При последующих изменениях таймингов нужно будет постояно проводить этот тест. Если плата не стартует значит мы достигли предела и нужно вернуться к прошлому стабильному таймингу. Для этого скидываем биос перемычкой и выставляем тайминг который был до не удачного запуска.
4. Далее одновременно снижаем тайминги tRP и tRCD.
5. Выставляем тайминг tRAS. Он должен быть равен или больше суммы таймингов "CAS Latency" и tRP. Если запуск системы не удался, то прибавляем к этому значению 2 и пробуем снова.
6. Ставим тайминг tWR. Он должен быть равен или больше "CAS Latency". Если "CAS Latency" нечётный то округляем его до первого чётного числа в большую сторону. Если стабильности нет, то прибавляем к таймингу 2.
7. tCWL. Должен быть равен "CAS Latency". Если же он нечётный то округляем в меньшую сторону.
8. tFAW ставим 16 не знависимо от других таймингов. Оно должно быть кратно 4. При нестабильности повышаем тайминг на 4. При стабильности снижаем на 4.
9. Ставим тайминг tRTP. Он должен быть равен таймингу tWR делёному на 2. Если стабильности нет, то повышаем тайминг tWR на 2 и tRTP на 1.
10. tRC должен быть равен или больше суммы tRAS и tRP. Если стабильности нет, то повышаем на 1.
11. tWTR должен быть равен разности tWR и tRTP. Можно понижать, но значение должно быть кратно 2 и не ниже 4.
12. tRRD должен быть равен или больше tFAW делёного на 4. В случае повышения нужно повысить tFAW на 4, а tRRD на 1.
13. Тайминг tRFC должен быть равен tRAS умноженого на 8. При не стабильности повышать на 40, а при стабильности снижать.
14. Refrash Rate ставим 32767 и тестируем. При нестабильности понижай его на 8192.

ДЛЯ ТЕХ У КОГО ДДР3:

Проверь скорость памяти и если она у тебя аномально низкая, то попробуй в биосе установить параметр "SET Throttlling Mode" (находится в IntelRCSetup -> Memory Configuration -> Memory Thermal) в значение OLTT

## 6. Выставляем шину ровно 100

1. Скачиваем [FIT](https://github.com/DmitryPonyn/BIOS_X99_China_Optimize/raw/refs/heads/main/software/fitc.zip).
2. Открываем FIT, принимаем условия использования и открываем в утилите дамп нашего биоса и в левой части программы разворачиваем ветки «ME Region» > «Configuration» > «Integrated Clock Controller» > «ICC Profile 0 — User Profile» > «DMI and PCIe Clock Settings»
3. Находим параметр «PCIe Spread Settings» и меняем его на «0.00%».
4. Сохраняем изменения (File > Save As...)
5. Прошиваем наш мод-биос любым подходящим способом
6. Открываем HWInfo\Aida64 или любой другой софт, показывающий значение системной шины и проверяем, что теперь она равна 100.00 Мгц.

## 6.2 На случай если шина всё равно не равна 100

Если значение шины меньше, чем 99.75 Гц — обычно причиной является  активный Hyper-V в Windows. Также занижать системную шину может компонент «Песочница Windows» (отключается аналогично Hyper-V) и включенная опция «целостность памяти» в разделе «изоляция ядра» (находится в «Центр безопасности защитника Windows» > «Безопасность устройства» > «Изоляция ядра»).

## 7 Настройки биоса

Некоторые настройки могут быть скрыты в твоём биосе, но их можно открыть через AMIBCP и прошить этот биос. Настройки указаны в стиле "путь>параметр>значение". Если есть какие-то предложиния или проблемы с какой-то настройкой биоса, то пиши в дискорд который указан в начале.

<details>
<summary>Advanced</summary>

PCI Subsystem\Settings>PCI Latency Timer> 160 !!но лучше найти своё значение на котором будет более лучший результат

PCI Subsystem\Settings>PCI-X Latency Timer> 160 !!но лучше найти своё значение на котором будет более лучший результат

PCI Subsystem\Settings>Above 4G Decoding>Enabled

PCI Subsystem\Settings\PCI Express Settings>Maximum Payload> максимальное значение

PCI Subsystem\Settings\PCI Express Settings>Maximum Read Request> максимальное значение

PCI Subsystem\Settings\PCI Express Settings>ASPM Support>Disabled

PCI Subsystem\Settings\PCI Express Settings>Link Training Retry>Disabled или 2 !!!При не старте системы или нестабильности с обоими значениями верни стандартное

PCI Subsystem\Settings\PCI Express GEN 2 Settings>Clock Power Management>Disabled

---------------------------------
</details>

<details>
<summary>IntelRCSetup</summary>

PCH Configuration\PCH SATA Configuration>Configure SATA as>AHCI !!!надеюсь у тебя это значение по стандарту было)

PCH Configuration\PCH SATA Configuration>SATA AHCI ALPM>Disabled

PCH Configuration\PCH SATA Configuration>SATA AHCI LPM>Disabled

PCH Configuration\PCI Express Configuration>PCI-E ASPM Support(GLOBAL)>Disable

PCH Configuration\PCI Express Configuration\PCI Express Root Port 1(до конца всех портов)>PCH-PCIE ASPM>Disable ASPM

PCH Configuration\PCI Express Configuration\PCI Express Root Port 1(до конца всех портов)>L1 Substates>Disable

PCH Configuration\PCI Express Configuration\PCI Express Root Port 1(до конца всех портов)>URR>Disable

PCH Configuration\PCI Express Configuration\PCI Express Root Port 1(до конца всех портов)>FER>Disable

PCH Configuration\PCI Express Configuration\PCI Express Root Port 1(до конца всех портов)>NFER>Disable

PCH Configuration\PCI Express Configuration\PCI Express Root Port 1(до конца всех портов)>CER>Disable

PCH Configuration\PCI Express Configuration\PCI Express Root Port 1(до конца всех портов)>PME SCI>Disable

IIO Configuration>Power down unused ports>no

IIO Configuration>PCI-E ASPM (GLOBAL)>Disable

IIO Configuration\IIO0 Configuration\(порт видеокарты или все)>PCI-E Port D-State>D0

IIO Configuration\IIO0 Configuration\(порт видеокарты или все)>MSI>Enable

QPI Configuration\QPI General Configuration>COD Enable>Disable

QPI Configuration\QPI General Configuration>Early Snoop>Disable

Memory Configuration>Enforce POR>Disable

Memory Configuration>ECC Support>Disable

Memory Configuration>MemTest>Disable

Memory Configuration>DRAM Mainternance Test>Disable

Memory Configuration>Rank Margin Tool>Disable

Memory Configuration>Attempt Fast Boot>Disable

Memory Configuration>Attempt Fast Cold Boot>Disable

Memory Configuration>MemTest On Fast Boot>Disable

Memory Configuration>RMT On Fast Boot>Disable

Memory Configuration\Memory Training>CMD Notmalization>Disable !!!test

Memory Configuration\Memory Thermal>Set Throttling Mode>OLTT или Disabled !!!test

Memory Configuration\Memory Thermal>Memory Power Settings Mode>Disabled

Memory Configuration\Memory Thermal>MDLL Off>Disabled

Memory Configuration\Memory Thermal>MEMHOT Throttling Mode>Disabled

Memory Configuration\Memory Thermal>Mem Electrical Throttling>Disabled

Memory Configuration\Memory Thermal\Memory Power Saving Advanced Options>CK in SR>Pulled Low !!!test

Memory Configuration\Memory Thermal\Memory Power Saving Advanced Options>CKE Throttling>Off !!!test

Memory Configuration\Memory Thermal\Memory Power Saving Advanced Options>Opportuninstic SR>Disabled !!!test

Memory Configuration\Memory Map>Channel Interleaving>Максимальное значение !!!test

Memory Configuration\Memory Map>Rank Interleaving>Максимальное значение !!!test

Memory Configuration\Memory RAS Configuration>Memory Power Management>Disable

Processor Configuration>Intel Enhanced Debug>Disable

Processor Configuration>Check CPU BIST Result>Disable !!!test

Processor Configuration>3StrikeTimer>Disabled !!!test

Processor Configuration>Machine Check>Disable

Advanced Power Management Configuration\CPU P State Control>EIST (P-States)>Enable

Advanced Power Management Configuration\CPU P State Control>Enery Efficent P-state>Disable

Advanced Power Management Configuration\CPU P State Control>Boot performance mode>Max Performance

Advanced Power Management Configuration\CPU C State Control>Enchanced Halt State (C1E)>Disable !!!test

Advanced Power Management Configuration\DRAM RAPL Configuration>DRAM RAPL Baseline>Disable !!!test

Advanced Power Management Configuration\DRAM RAPL Configuration>Override BW_LIMIT_TF>0 !!!test

Advanced Power Management Configuration\CPU - Advanced PM Tuning\Energy Perf BIAS>Energy Performance Tuning>Disable

Advanced Power Management Configuration\CPU - Advanced PM Tuning\Energy Perf BIAS>Energy Performance BIAS setting.>Performance

---------------------------------
</details>

## 7.1 Ядра

Возможно ты владелец дохренаядерных ксеонов по типу 2696v3/2699v3/2697v3 и ты играешь в игры. Если зайти в игру с их стоковым количеством ядер, то даже с -100mv офсетом на ядра ты не получишь максимальной частоты на все. Как пример мой 2696v3 имеет максимально стабильный офсет -75mv на ядра и -85mv на кеш и при загрузке на все ядра он может выдать только 3.3ггц, но под игры конечно столько ядер не нужно, им более важна частота на ядро и на этом мы можем сыграть.

1. Заходим в биос в вкладку "IntelRCSetup\Processor Cofiguration"
2. Выключаем Hyper-Threading[ALL] и в вкладке "IntelRCSetup\Processor Cofiguration\Per-Socket Configuration\CPU Socket 0 Configuration" в поле Cores Enabled выставляем 12 ядер.
3. Перезагружаемся и смотрим результат в играх.

Чем больше получится офсет тем лучше будут держаться частоты в играх. Так же можно протестить конфигурацию с включёным Hyper-Threading и 10 ядрами ибо в некоторых играх она может дать больше кадров.

Для работы же лучше это всё не трогать, а оставить по стоку.
