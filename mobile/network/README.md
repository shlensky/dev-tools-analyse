## Записать и сохранить в HAR архив профиль загрузки ресурсов при открытии страницы

[Прикрепил файл](./lifehacker.ru.har)

## Дублирование ресурсов

Несколько раз подключается код рекламных сетей, но на этот раз они отменяются по таймауту.
Например `adsbygoogle.js` отменяется спустя 4 секунды.
 
Приложил скриншоты в папке ["дублирование ресурсов"](./duplicates)

## Лишний размер ресурса

есть не минимизированные ресурсы, например
* https://lifehacker.ru/wp-content/themes/lifehacker/static/js/vendors.min.js?ver=1.3.12
несмотря на название, файл неполностью минимизирован.

Еще несколько не минимизированных файлов:
* https://lifehacker.ru/wp-content/plugins/lh-twister/assets/app.js?ver=7
* https://lifehacker.ru/wp-content/plugins/lh-appbox/css/styles.min.css?ver=17
* https://lifehacker.ru/wp-content/plugins/responsive-lightbox/js/front.js?ver=1.7.2
* +есть еще 

## Медленно загружающиеся ресурсы

* 34.07s https://cdn.lifehacker.ru/wp-content/uploads/2019/09/1920_1569244229-1140x570_1569700433.jpg
* 28.06s https://lifehacker.ru/wp-content/uploads/2019/08/B1_1567153464.jpg
* 13.18s https://cdn.jsdelivr.net/npm/yandex-metrica-watch/tag.js

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

