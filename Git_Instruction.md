# Работа с Git ![Git logo](img/1color-darkbg%402x.png)

## <u>1. Проверка наличия установленного Git</u>

В терминале выполнить команду `git version`
Если Git установлен, появится сообщение с информацией о версии программы. Иначе будет сообщение об ошибке. Если выяснилось, что используется устаревшая версия, то для обновления (для Windows) вводим в терминале команду `git update-git-for-windows`

## <u>2. Установка Git</u>

Загружаем последнюю версию Git с официального сайта по адресу:

https://git-scm.com/downloads

Устанавливаем с настройками по умолчанию.

## <u>3. Настройка Git</u>

При первом использовании Git необходимо представиться. Для этого в терминале надо внести две команды:

```
git config --global user.name "Your name"
git config --global user.email "post@example.com"
```

## <u>4. Создание репозитория</u>

Создать репозиторий можно двумя способами:

1. **`Инициализация`**. В терминале переходим к папке, в которой хотим создать репозиторий. Выполняем команду

<i style="color:green; font-family:courier; font-size:20px">git init</i>

При этом будет создана папка `.git`, которая является скрытой и будет видна только при соответствующей настройке операционной системы.
В этой папке хранится вся информация о проекте и его изменениях.

2. **`Клонирование`**. Репозиторий создаётся путём создания копии другого репозитория. Способ будет рассмотрен в следующих лекциях.

## <u>5. Запись изменений в репозиторий</u>

Запись изменений репозитория может варьироваться в зависимости от конкретной ситуации состоит из нескольких этапов:

### 1) Проверка статуса репозитория

Для проверки статуса (состояния) репозитория вводим команду

<i style="color:green; font-family:courier; font-size:20px">git status</i>

При этом в терминал выводится:

- отслеживается ли репозиторий (если, например, репозиторий не инициирован)
- информация о том, в какой ветке выполняются действия
- информация об отслеживаемых файлах и их статусе, такие как:

1. все текущие файлы отправлены в хранилище
2. перечень модифицированных файлов, которые необходимо поставить в очередь на сохранение. Они выделяются красным цветом.
3. перечень модифицированных файлов, уже поставленных в очередь на сохранение. Они выделяются зелёным цветом.
4. подсказки о выполнении действий, которые в данной ситуации необходимы
   > Возможна упрощённая команда `git status -s` , которая отображает статус измененных файлов буквой М (красной, если изменённые файлы не поставлены в очередь на сохранение, зелёной, если они готовы к сохранению и двумя буквами М (ММ) - одной красной и одной зелёной, если файл добавлен в очередь на сохранение командой `git add`, но не сохранён, и в этой ситуации файл дополнительно был изменен, но не добавлен в очередь на сохранение. В этой ситуации следует этот изменённый файл поставить в очередь на сохранение командой `git add <имя файла>`)

_О постановке в очередь на сохранение смотри в следующем пункте_

### 2) Добавление файлов в очередь на сохранение

Для того, чтобы поставить изменённые файлы в очередь на сохранение, необходимо в терминале ввести следующую команду:

<i style="color:green; font-family:courier; font-size:20px">git add <Имя файла> <Имя файла></i>
Все файлы, которые необходимо поставить в очередь, перечисляются через пробел и должны быть указаны со своими расширениями

> Для внесения в список `всех` изменённых файлов удобно использовать универсальную команду: <i style="color:green; font-family:courier; font-size:20px">git add .</i> Точка обозначает _"все файлы"_.

После выполнения команды `git add`, если проверить статус командой `git status`, имена выбранных файлов будут выделены <span style="color:green">зелёным</span> цветом. Если не все файлы были включены в список на сохранение, то цвет невыбранных файлов останется <span style="color:red">красным</span>

Удалить файл из очереди на сохранение можно командой

<i style="color:green; font-family:courier; font-size:20px">git rm --cached Имя файла</i>

### 3) Просмотр изменений в файлах, поставленных в очередь

До внесения файлов в очередь на запись в коммит можно просмотреть, какие внесены изменения в эти файлы командой

<i style="color:green; font-family:courier; font-size:20px">git diff</i>

Добавленное содержимое будет начинаться со знака `+` и выделено <span style="color:green">зелёным</span> цветом.
Удаленное из файла содержимое будет начинаться со знака `-` и выделено <span style="color:red">красным</span> цветом.

### 4) Сохранение файлов из очереди в коммит

Для сохранения (фиксации) файлов из очереди в хранилище необходимо ввести команду:

<i style="color:green; font-family:courier; font-size:20px">git commit -m "<Комментарий>"</i>

> Если сохраняем уже имеющиеся файлы (то есть, старые версии этих файлов уже имеются в хранилище), то можно воспользоваться командой  
> <i style="color:green; font-family:courier; font-size:20px">git commit `-am` "<Комментарий>"</i>

> Что автоматически ставит эти файлы в очередь (без использования команды `git add`) и отправляет их в хранилище.
> Следует учесть, что таким образом мы не сможем сохранить файлы выборочно, а сохраняет сразу все изменённые файлы.

## <u>6. Просмотр истории коммитов</u>

Для просмотра истории коммитов данного репозитория следует ввести команду

<i style="color:green; font-family:courier; font-size:20px">git log</i>

Команда выводит информацию о всех сохранениях, включая их `ID` и комментарии, что позволяет ориентироваться в истории сохранений и переходить к любому из них, используя их `ID`. Подробнее о переходе между коммитами можно посмотреть в следующем Разделе 7.

> Если список сохранений (коммитов) достаточно большой, то можно воспользоваться этой командой с ключом "одной строкой":

> <i style="color:green; font-family:courier; font-size:20px">git log --oneline</i>

Кроме того, можно вывести не все, а несколько последних коммитов, указав их количество в качестве ключа:

<i style="color:green; font-family:courier; font-size:20px">git log -2</i>

## <u>7. Перемещение между сохранениями</u>

При необходимости перейти к какому-нибудь из прошлых сохранений (например, чтобы создать от него ответвление, или, как обычно называют, ветку), используем команду

<i style="color:green; font-family:courier; font-size:20px">git checkout ID</i>

где используем ID сохранения, полученный в предыдущем Разделе 6.

> Команда не будет работать, пока не будут выполнены сохранения всех изменённых файлов.

Чтобы вернуться на вершину основной ветки (обычно это master) и продолжить работу с проектом, вводим команду

<i style="color:green; font-family:courier; font-size:20px">git checkout master</i>

## <u>8. Несколько советов по работе с Git</u>

> _Для очистки окна терминала следует ввести команду_ `clear`

> _Для возврата управления терминалом после вывода в него информации при выполнении какой-нибудь команды, следует нажать клавишу `Q`. При этом, клавиатура должна быть переключена на английскую раскладку._

> _Для того, чтобы скрыть/показать терминал, используем горячие клавиши `Ctrl+J`_

> _Для изменения коммертария уже сохранённого коммита можно использовать команду `git rebase -i HEAD~4` Для примера выбрано к исправлению 4 последних комментария. В открывшемся редакторе для коммитов, в которых требуется изменить комментарий, в начале строки об этом коммите меняем `pick` на `r`, сохраняем и закрываем редактор, который автоматически открывается вновь, но уже с возможностью откорректировать нужный комментарий. Корректируем, сохраняем, закрываем редактор. Задача выполнена._ > _Команда работает только если нет несохранённых изменений_

> _Для установки редактора по умолчанию вводим в терминале строку `git config --global core.editor Редактор`. Редактор может быть, например, notepad, и команда будет выглядеть таким образом:
> `git config --global core.editor notepad`_

### _Выделение блока кода в соответствие синтаксису указанного языка. В примере использован язык Javascript_

```JS
while(a < 0) {
console.log(a)
}
```

## <u>9. Использование псевдонимов</u>

<i style="color:green; font-family:courier; font-size:20px">git config --global alias.chk "checkout"</i>

```
где:
chk - придуманное нами сокращение для команды checkout
"checkout" - строка, вместо которой мы используем chk
```

После однократного ввода этой команды, в дальнейшем можно будет вводить git chk [ID коммита] или git chk [Имя ветки] вместо git checkout [ID коммита] или git checkout [Имя ветки] соответственно.

## <u>10. Запрет на сохранение файлов и папок (файл .gitignore)</u>

Большие файлы, изображения, видео хранить на Git - это плохой тон. К тому же они просто загружают хранилище. Поэтому, для того, чтобы при сохранении проекта эти файлы не передавались в хранилище, используют файл, в котором создаётся список файлов и папок, не предназначенных для отправки. Этот файл должен иметь имя `.gitignore`. Каждый элемент списка в нём вводится с новой строки. Если это папка, то перед её именем должен стоять слэш `"/"`, если это отдельный файл во вложенной папке, то должен прописываться путь к нему от корневой папки проекта, включая вложенную папку.

## <u>11. Клонирование репозитория</u>

Одним из способов создания репозитория является его клонирование из другого репозитория, в том числе из находящегося в удалённом ресурсе. Используется команда

<i style="color:green; font-family:courier; font-size:20px">git clone ссылка</i>

Следует иметь ввиду, что клонируются не только сами файлы, но и все их версии с историей изменений. Так же, клон имеет имя оригинального репозитория. Чтобы клонировать репозиторий и присвоить ему другое имя, следует ввести команду

<i style="color:green; font-family:courier; font-size:20px">git clone ссылка новое_имя</i>

где новое_имя - это может быть целый путь к создаваемой при этом папке, а имя этой папки будет новым именем репозитория.

## <u>12. Удаление репозитория</u>

Что делать, если репозиторий уже не нужен и его требуется удалить?
Такой команды в Git не существует. Это можно сделать средствами операционной системы - удалить из папки проекта папку с репозиторием. Она является скрытой папкой и имеет название `.git`

## <u>13. Просмотр веток репозитория</u>

Для того, чтобы посмотреть, какие ветки существуют в данном репозитории, требуется ввести следующую команду:

<i style="color:green; font-family:courier; font-size:20px">git branch</i>

После этого в терминале будет выведен список существующих в репозитории веток, активная будет выделена <span style="color:lightgreen">зелёным</span> цветом и отмечена звёздочкой `*`

## <u>14. Создание новой ветки</u>

Для того, чтобы создать новую ветку в репозитории, требуется ввести команду:

<i style="color:green; font-family:courier; font-size:20px">git branch Имя-новой-ветки</i>

Ветка будет создана, но не станет активной. Для того, чтобы вносить изменения во вновь созданную ветку, требуется сделать её активной, используя команду перехода в другую ветку (_`смотри раздел 15`_).

Если использовать с командой `checkout` ключ `-b`, то команда примет вид

<i style="color:green; font-family:courier; font-size:20px">git checkout -b Имя-новой-ветки</i>

и, не только создаст новую ветку, но и сделает её активной

## <u>15. Переход в другую ветку</u>

Переход в другую ветку выполняется той же командой, которой мы переходим к другому коммиту (сохранению) `("смотри Раздел 7")`, только вместо ID коммита мы вводим имя нужной ветки

<i style="color:green; font-family:courier; font-size:20px">git checkout Имя-требуемой-ветки</i>

## <u>16. Слияние веток репозитория</u>

После того, как работа в отдельной ветке будет закончена, её результат, как в будущем и результат других отдельных веток проекта, следует перенести в основную ветку. Для этого, находясь в основной ветке, используем команду

<i style="color:green; font-family:courier; font-size:20px">git merge Имя-присоединяемой-ветки</i>

Содержимое из присоединяемой ветки сольётся с содержимым основной автоматически, если не возникнет конфликт веток _`(про разрешение конфликтов смотрим в Разделе 17)`_
После слияния, полученный результат слияния следует отправить в хранилище _`(Раздел 2 и раздел 4 этого руководства)`_.

## <u>17. Конфликты при слиянии и их устранение</u>

При слиянии текущей и боковой веток могут возникнуть конфликты. В большинстве случаев система контроля версий проводит слияние веток автоматически, без вмешательства человека. Однако, в ситуации, когда изменения были произведены в обеих ветках в тех же строчках, система предоставляет возможность человеку разрешить конфликт, а именно, предлагает ему сделать выбор:

- оставить вариант основной ветки;
- оставить вариант присоединяемой ветки;
- оставить оба варианта;
- предлагает сравнить оба варианта и отредактировать их.

После предпринятых действий по устранению конфликта, для завершения слияния следует выполнить сохранение полученной в результате этих действий основной ветки командами `git add .` и `git commit -m "Комментарий"`.

## <u>18. Удаление слитой ненужной ветки</u>

После слияния с основной веткой, боковая ветка может оказаться больше ненужной. Такую ветку можно удалить из репозитория командой

<i style="color:green; font-family:courier; font-size:20px">git branch -d Имя-удаляемой-ветки</i>

При этом основная ветка должна быть активной и выполнены сохранения (коммиты) в удаляемой ветке.

## <u>19. Удаление не слитой ненужной ветки</u>

Возможна ситуация, когда была создана дополнительная ветка, с ней выполнена определённая работа по наполнению информацией, но, по той или иной причине, эта информация оказалась не нужна. Удалить эту ветку способом, описанном в Разделе 18, с использованием команды `"git branch -d Имя-удаляемой-ветки"` не получится, так как ветка не была слита с основной веткой. В такой ситуации требуется применить ключ `"-D"`, соответственно, введя команду

<i style = "color:green;font-family:courier;font-size:20px">git branch -D Имя-удаляемой-ветки</i>

Таким образом, такая ветка будет удалена.

# Создание запроса PullRequest

В ситуации, когда над одним проектом работает несколько сотрудников, у каждого из них существует необходимость внесения в репозиторий проекта результаты своей работы. При этом, добавление должно контролироваться, чтобы эти результаты не были подвергнуты изменению при сохранении файлов другого члена команды. Впрочем, верно и обратное. В сервисе `GitHub` существует механизм, позволяющий членам команды выполнять свою работу в тесном взаимодействии друг с другом, причём, при безусловном сохранении результатов работы каждого.
Этот механизм реализован, в частности, с помощью системы создания `Pull request`-ов. Она заключается в следующем:

## <u>20. Копирование репозитория проекта в аккаунт сотрудника на GitHub `(Fork)`.</u>

У каждого работника должен быть свой аккаунт на сервисе GitHub. Войдя в репозиторий проекта компании на сервисе GitHub, сотрудник нажимает кнопку `Fork `в верхнем правом углу сервиса. Это действие создаёт копию репозитория компании в аккаунте работника на GitHab.

## <u>21. Клонирование копии проекта из аккаунта сотрудника на его локальный компьютер `(Clone)`.</u>

В своём репозитории на сервисе GitHub сотрудник, нажимая на кнопку `Code`, на закладке `HTTPS` копирует адрес (`Скопированный-адрес`) копии репозитория проекта компании.
На локальном компьютере в программе VS Code сотрудник создаёт (или открывает) папку, которая не является репозиторием. В терминале, находясь в этой папке, сотрудник вводит команду

<i style = "color:green;font-family:courier;font-size:20px">git pull Скопированный-ранее-адрес</i>,

в результате этого у него в открытой папке в программе VS Code появляется папка с копией репозитория компании. В терминале он переходит в папку этого репозитория, используя команду

<i style = "color:green;font-family:courier;font-size:20px">cd имя-папки-скопированного-репозитория</i>

Далее, в этом репозитории можно выполнять все команды системы Git на локальном компьютере. Первое, что надо сделать - это посмотреть статус этого репозитория, убедившись, что он существует и не имеет каких-либо проблем.

## <u>22. Создание отдельной ветки на локальном компьютере для внесения в нее результатов работы сотрудника `(Branch)`.</u>

Категорически возбраняется вносить изменения непосредственно в основную ветку репозитория компании. Необходимо создать собственную отдельную ветку, в которую и вносить результаты своей работы. Создание ветки описано в этом руководстве в `Разделе 14` - Создание новой ветки.

## <u>23. Сохранение результатов работы сотрудника в его репозитории на GitHub `(Push)`.</u>

Выполнение работы в репозитории должно сопровождаться по мере необходимости созданием сохранений ветки командой `commit` (См. в этом руководстве Раздел 5 подраздел 4 - Запись изменений в репозиторий).
Завершив работу по внесению, а, возможно, и по корректировке результатов своей работы в отдельной ветке репозитория компании на локальном компьютере и сделав итоговое сохранение (`commit`), сотрудник может отправить этот результат в свой репозиторий на сервисе GitHub командой ` git push`. Причём, при первой отправке следует использовать команду

<i style = "color:green;font-family:courier;font-size:20px">git push -u origin имя-ветки</i>

В дальнейшем программа запоминает ветку как ветку по умолчанию, и отправлять данные можно сокращенной командой

<i style = "color:green;font-family:courier;font-size:20px">git push</i>

## <u>24. Создание запроса на добавление результатов работы сотрудника в репозиторий проекта `Pull request`.</u>

После отправки сохранённой работы в свой репозиторий командой `push`, как было описано в `Разделе 23`, переходим в свой репозиторий на GitHub, где должна появиться кнопка `Compare & pull request`. После нажатия на эту кнопку в репозитории открывается закладка с формой отправки pull request-а, где есть возможность озаглавить его и написать комментарий при необходимости (лучше это сдалать, чтобы хозяин репозитория сразу мог понять что за дополнения к нему направлены). После завершения этих операций нажимаем кнопку Create pull request. Всё. Pull request отправлен на рассмотрение.


## <u>25. Особенности при работе с проектами `Java`.</u>

1. Создаём папку, в которой предполагается хранение репозитория с несколькими проектами
   - в папке __НЕ СОЗДАЁМ !!!__ рабочую область VSCode;
   - создаём репозиторий на `GitHub` и привязываем к нему нашу созданную папку обычным образом (см. выше в этой инструкции)
   - в папке можем создавать подпапки, например, Seminar01. Seminar02 и т.д. (если это требуется планируемой структурой репозитория)
   - в подпапках также __НЕ СОЗДАЁМ !!!__ рабочую область VSCode;
   - в папке, или подпапке создаём проект средствами VSCode:
      1. Ctrl+Shift+P (вызываем рабочее меню);
      2. Выбираем/вводим Java: Create Java Project
      3. Выбираем/вводим No build tools (work with source code directly without any build tools)
      4. В появившемся окне Windows выбираем папку/подпапку, в которой будет размещаться создаваемая папка с проектом
      5. Вводим (Input a Java Project name) имя создаваемого проекта (а также это будет и именем создаваемой папки проекта)
      6. Создастся проект, и в папке src надо открыть файл App.java, что, через несколько секунд приведёт к сообщению "Показать проект", на которое требуется "кликнуть" левой кнопкой мыши. В левом боковом окне VSCode появится структура проекта и, выше, структура просматриваемого в основном окне файла. После создания своих файлов проекта, файл App.java можно удалить - он не нужен.
      7. В папке проекта уже удобно сохранить рабочую область VSCode. 
      8. Все создаваемые таким образом проекты будут храниться в одном репозитории, который вы создали изначально.
      9. Следует иметь ввиду, что в каждой из папок проекта будет создаваться папка .vscode, которая будет хранить коммиты данного конкретного проекта, к которым не будут добавляться изменённые файлы из других проектов общей папки этого репозитория (для сохранения изменённых файлов других проектов следует открывать в VSCode соответствующие проекты).
      10. Не следует забывать открывать общую __ПАПКУ__ репозитория в VSCode (__НЕ рабочую область__, которую мы не должны были в ней создать) и также коммитить изменения в ней (например, там могут быть новые подпапки).
      11. 