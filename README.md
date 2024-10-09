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
<summary>Анлок турбобуста 26xx v3 + FIVR</summary>

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

Далее надо определиться с тем, хотим ли мы найти максимальное значение андервольта или нет. Если не хотим то 

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
