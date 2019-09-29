## Записать и сохранить в HAR архив профиль загрузки ресурсов при открытии страницы

[Прикрепил файл](./lifehacker.ru.har)

## Дублирование ресурсов

Видимо несколько раз подключается код рекламных сетей, и несколько раз загружается их код.
Приложил скриншоты в папке ["дублирование ресурсов"](./duplicates)

## Лишний размер ресурса

есть не минимизированные ресурсы, например
* https://lifehacker.ru/wp-content/themes/lifehacker/static/js/vendors.min.js?ver=1.3.12
несмотря на название, файл не минимизирован.

Еще несколько не минимизированных файлов:
* https://lifehacker.ru/wp-content/plugins/lh-twister/assets/app.js?ver=7
* https://lifehacker.ru/wp-content/plugins/lh-appbox/css/styles.min.css?ver=17
* https://lifehacker.ru/wp-content/plugins/responsive-lightbox/js/front.js?ver=1.7.2
* +есть еще 

## Медленно загружающиеся ресурсы

* 594ms https://cdn.lifehacker.ru/wp-content/uploads/2018/07/25-ideJ-dlya-byudzhetnogo-svidaniya_1531434357-1600x800.jpg
* 394ms https://cdn.lifehacker.ru/wp-content/uploads/2017/08/20-tovarov-s-AliExpress-dlya-tyoploj-i-uyutnoj-oseni_1569589045-1600x800.jpg
* 364ms https://lifehacker.ru/wp-content/plugins/lh-widgets/js/viewed.js?ver=58

Это топ3 ресурса по времени загрузки, но там еще много ресурсов с похожим временем загрузки.

## Ресурсы, блокирующие загрузку

* https://lifehacker.ru/wp-includes/js/jquery/jquery.js?ver=1.12.4
* https://lifehacker.ru/wp-includes/js/jquery/jquery-migrate.min.js?ver=1.4.1
* https://lifehacker.ru/wp-content/plugins/lh-spoilers/inc/bbspoiler.js?ver=5.1.2


и прочие скрипты которые подключены в `<head></head>`
было бы логично перенести подключение скриптов к конец страницы (перед `</body>`)
либо добавить `defer`.

## Что-то ещё

Полезно объединять все `.css`, и `.js` файлы в бандлы, что бы минимизировать кол-во запросов к серверу.

