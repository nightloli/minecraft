Майнкрафт, особенно с модами — очень требовательная к ресурсам ПК игра, анон. Если у тебя слабая печка, то ты скорее всего окажешься не доволен производительностью игры. В этой статье специально для тебя были собраны все возможные рекомендации по оптимизации Minecraft, с которыми в кубач можно будет поиграть даже на некропк. Впрочем, пользуйся вдумчиво и аккуратно: некоторые из них могут оказать обратный эффект и лишь усугубить ситуацию.  

---

## Оптимизация аргументов запуска

Аргументы запуска (_**JVM флаги**_) — отличный способ облегчить жизнь твоему сборщику мусора и в целом начать использовать ресурсы комьютера более эффективно. Учти, что некоторым флагам может понадобиться полная версия джавы, т. е. **[`JDK`](https://adoptopenjdk.net/)**. (или **[`серверная JRE`](https://www.oracle.com/java/technologies/javase-server-jre8-downloads.html)**)  
#
* Оптимизация сборщика мусора **G1GC** (_Aikar's arguments_): [`клик`](https://aikar.co/2018/07/02/tuning-the-jvm-g1gc-garbage-collector-flags-for-minecraft/)   
* Оптимизация аргументов для клиента: [`клик`](https://cwelth.com/manuals.php?mid=2)[¹](https://docs.google.com/document/d/1Y9bijAyuXMlbCs9ttR5X1DOGzK-yq353zS70X01M9hY/edit?usp=sharing) [²](https://pastebin.com/VX5K9NW7) [³](https://gist.github.com/nightloli/36a6ac3558449452b121db030c86ee27)  
* Матчасть про **JVM флаги** на хабре: [`клик`](https://habr.com/ru/post/160049/)
#
Флаги, не описанные в статьях выше:
* **`-XX:+UseStringDeduplication`** — GC будет пытаться экономить память, уничтожая повторяющиеся строки, в обмен на большее использование процессора из-за большего объёма сканируемой памяти. Потенциально может cэкономить до 13,5% оперативной памяти.
* **`-XX:-DontCompileHugeMethods`** — отключает лимит на длинну методов, которые JVM может скомпилировать. Пруфов пользы и вреда нет.
* **`-server`** — меняет некоторые дефолтные значения JVM флагов и использует другой компилятор байткода, применяющий больше оптимизаций при компиляции. ([`источник`](https://stackoverflow.com/questions/198577/real-differences-between-java-server-and-java-client))
* **`-Dorg.lwjgl.util.NoChecks=true`** — отключает state tracking и дополнительные проверки во время игры, за счёт чего даёт немного производительности.
* **`-Dforge.forceNoStencil=true`** — у некоторых людей лечит лаги при загрузке чанков на 1.7.10. ([`источник`](https://forum.feed-the-beast.com/threads/1-7-10-chunk-generation-lag.48182/page-3))

## Оптимизация с помощью модов

С помощью модификаций можно добавлять не только килотонны нового контента, но и заставлять игру работать быстрее.  

---
### Оптимизация новейшей версии (1.16.1)

| Мод | Описание |
|---|---|
|[OptiFine](https://optifine.net/downloads)|Расширенные настройки графики, оптимизация для некропк, шейдеры для йобапк.|
|[Phosphor](https://www.curseforge.com/minecraft/mc-mods/phosphor)|Заметные оптимизации светового движка.|
|[Lithium](https://www.curseforge.com/minecraft/mc-mods/lithium)|Значительные бусты физики, загрузки чанков, ИИ мобов, редстоуна, etc.|
|[Sodium](https://www.curseforge.com/minecraft/mc-mods/sodium)|ВНЕЗАПНО релизнулся. По заявлению автора, бустит фпс в 400%, что правда.|
|[OptiFabric](https://www.curseforge.com/minecraft/mc-mods/optifabric)|Без этой штучки фабрик и оптифайн не дружат.|
|[FastFurnace](https://www.curseforge.com/minecraft/mc-mods/fast-furnace-for-fabric) и [FastWorkbench](https://www.curseforge.com/minecraft/mc-mods/fastbench-for-fabric)|Кэширование рецептов верстака и печки, что способствует экономии процессорного времени. Эффект заметен лишь на больших серверах с множеством баз. В сингле вряд ли почувствуется.|
> **TIP:** В новейших версиях (1.14+) появился новый мод-лоадер: `Fabric`. Он смог составить конкуренцию всем привычному Forge, что является показателем и огромным достижением, и к фабрику уже тоже имеются оптимизационные моды.  

---

### Оптимизация 1.12.2
|Мод|Описание|
|---|---|
|[OptiFine](https://optifine.net/downloads)|Расширенные настройки графики, оптимизация для некропк, шейдеры для йобапк.|
|[Phosphor](https://www.curseforge.com/minecraft/mc-mods/phosphor-forge)|Заметные оптимизации светового движка.|
|[VanillaFix](https://www.curseforge.com/minecraft/mc-mods/vanillafix)|Различные багфиксы, а ещё игра не будет закрываться из-за крашей. Musthave!|
|[FoamFix](https://www.curseforge.com/minecraft/mc-mods/foamfix-optimization-mod)|Значительная экономия ОЗУ посредством хитрого шаманства.|
|[AI Improvements](https://www.curseforge.com/minecraft/mc-mods/ai-improvements)|Оптимизация ИИ мобов путём кастрирования патфайндинга.|
|[Surge](https://www.curseforge.com/minecraft/mc-mods/surge)|Ускорение загрузки игры и пара багфиксов.|
|[Multithreaded Noise](https://www.curseforge.com/minecraft/mc-mods/multithreaded-noise)|Многоядерная генерация перлин нойза; чем больше ядер у процессора — тем лучше.|
|[Performant](https://www.curseforge.com/minecraft/mc-mods/performant)|Различные оптимизации патфайндинга, оптимизация мобов (и энтитей в целом).|
|[Unloader](https://www.curseforge.com/minecraft/mc-mods/unloader)|Более агрессивная выгрузка измерений, что в теории фиксит утечки памяти.|
|[TexFix](https://www.curseforge.com/minecraft/mc-mods/texfix)|Экономия памяти при использовании детализированных ресурспаков. (если не используешь их, мод тебе не нужен.|
|[BetterFps](https://www.curseforge.com/minecraft/mc-mods/betterfps)|Оптимизация рендеринга путём повышения эффективности  sin() и cos() функций. (этим по сути дублирует функционал OptiFine, но у мода есть и уникальные фичи, поэтому он тут.|
|[Chunk-Pregenerator](https://www.curseforge.com/minecraft/mc-mods/chunkpregenerator)|Быстрая прегенерация чанков мира в определённом радиусе, очень спасает от лагов во время путешествий в неизученные места. А ещё имеет няшный интерфейс и даже умеет в ретроген!|
|[FastFurnace](https://www.curseforge.com/minecraft/mc-mods/fastfurnace) и [FastWorkbench](https://www.curseforge.com/minecraft/mc-mods/fastworkbench)|Кэширование рецептов верстака и печки, что способствует экономии процессорного времени. Эффект заметен лишь на больших серверах с множеством баз. В сингле вряд ли почувствуется.|

---

### Оптимизация 1.7.10
|Мод|Описание|
|---|---|
|[OptiFine](https://optifine.net/downloads)|Расширенные настройки графики, оптимизация для некропк, шейдеры для йобапк.|
|[BetterFps](https://www.curseforge.com/minecraft/mc-mods/betterfps)|Оптимизация рендеринга путём повышения эффективности  sin() и cos() функций. Дублирует функционал OptiFine, но есть и уникальные фичи.|
|[Chunk-Pregenerator](https://www.curseforge.com/minecraft/mc-mods/chunkpregenerator)|Позволяет заранее генерировать чанки мира, чем спасает от лагов во время путешествий в неизученные места. А ещё имеет няшный GUI и даже умеет в ретроген. (На 1.7.10-версию GregoriousT советует [этот патч для ваниллы](https://www.curseforge.com/minecraft/mc-mods/careful-cast-corrector-ccc) и [этот патч](https://www.curseforge.com/minecraft/mc-mods/chicken-chunk-patcher), если установлен Forge Multipart, чтобы избежать крашей во время прегенерации. [Источник](https://gregtech.mechaenetia.com/downloads/gregtech_1.7.10/index.html).|
|[FastCraft](https://www.curseforge.com/minecraft/mc-mods/fastcraft)|Много разных ощутимых оптимизаций. С OptiFine работает только последняя версия, в которой, ради совместимости с оптифайном, чуть порезали оптимизаций. Так что, если не пользуетесь оптифайном, выбирайте предпоследнюю версию.|
|[Thaumic Fixer](https://www.curseforge.com/minecraft/mc-mods/thaumic-fixer)|Фиксит лаги во время сканирования таумометром в Thaumcraft. Требует, очевидно, Thaumcraft. Используйте на свой страх и риск, ведь в комментариях к моду пишут о множестве проблем и багов.|

> **TIP:** Некоторые моды имеют возможность отключить особо тяжёлый функционал, и снизив тем самым нагрузку на ПК.  
Например, в конфиге Lycanites Mobs есть опции Disable Model Alpha и Model Multipass, которые облегчат жизнь твоему ПК, порезав рендер моделек ликанитов и альфа-канал. А разработчик Twilight Forest в конфиге мода вообще отвёл отдельную секцию для настроек производительности. Подобное снисхождение для обладателей некропекарен имеется во многих модах, анон, не ленись читать конфиги!

## Прочие оптимизации

### **Обновление библиотек старых версий**

Если ты играешь на версиях до примерно 1.12.2, то для повышения производительности и исправления багов стоит обновить библиотеки, которые использует майнкрафт.

На официальной вики майнкрафта есть [такой гайд](https://minecraft.gamepedia.com/Tutorials/Update_LWJGL_(Legacy)), но в новых майнкрафтах используется последний nightly билд lwjgl, а не который по ссылке в вики. Ночной билд можно найти по [этой ссылке](https://github.com/asanetargoss/lwjgl/releases/tag/nightly-20161208), а также, помимо путей из вики, части lwjgl лежат в ```.minecraft/libraries/org/lwjgl/lwjgl```.

Также можно обновить [vecmath](https://mvnrepository.com/artifact/javax.vecmath/vecmath), который лежит в ```.minecraft/libraries/java3d/vecmath```.

### **Отключение логов**

Если ты — счастливый обладатель медленного HDD в 2020 году, то может помочь отключение логгирования в майнкрафте. Для этого добавьте к аргументам запуска **`-Dlog4j.configurationFile=log4j2.xml`** и создайте в директории игры файл **`log4j2.xml`** со следующим содержанием:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Configuration status="ERROR" packages="com.mojang.util">
    <Loggers>
        <Root level="OFF" additivity="false">
        </Root>
    </Loggers>
</Configuration>
```
#
### **Ram-диск**

Если у тебя ещё остаётся оперативная память, после запуска майнкрафта, ты можешь перенести мир на ram-диск. Также я слышал слух, про то, что имеет смысл перенести JVM на рамдиск и пользуюсь этим советом, но доказательств пользы у меня нет.

> **TIP:** Не пользуйся фичей, если собираешься прегенерировать чанки! Оперативная память закончится моментально. Сейв, с оверворлдом, прогруженным на радиус ~300 чанков, запросто съедает больше гигабайта места! И в целом ей стоит пользоваться, только если после запуска майнкрафта и всего, нужного вам во время игры, у вас остаётся гигабайт-другой оперативки: если вы выделите недостаточно места на рамдиске под мир, то потеряете часть своего драгоценного прогресса по игре, когда сейв заполнит весь рамдиск, а если выделите всё, что у вас есть, и оперативка заполнится, то будете сидеть перед замершим компом и ждать, пока OOMKiller прихлопнет вам майнкрафт!

В Linux используется tmpfs и автобекап. [Этот гайд](https://wiki.archlinux.org/index.php/Improving_performance#Relocate_files_to_tmpfs) хоть и находится на вики арча, но подойдёт для 99% линуксов.

Для Windows есть [огромный зоопарк](https://en.wikipedia.org/wiki/List_of_RAM_drive_software#Microsoft_Windows) какого-то софта для рамдисков, тот, кто сейчас это пишет, не может ничего порекомендовать из него.
