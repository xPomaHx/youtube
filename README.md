# youtube
Развернуто тут http://o99920au.beget.tech/
> Проверка гипотизы о том реально ли хостить видео на google drive.
Гугл позволяет после разшаривания получать файл по прямой стабильной ссылке, например, по ссылке
https://drive.google.com/open?id=19HczNyXge0B1tjffEmwUeBsjFfuTQU4e
отдается html предлагающая скачать, а по ссылке
https://drive.google.com/uc?id=19HczNyXge0B1tjffEmwUeBsjFfuTQU4e
отдается непосредственно сам файл, значит можно сунуть в элемент <video> и браузер откроет видео в плеере несмотря на cors

В результате всё работает с ограничениями, если человек не залогинен в гугле, то файлы будут отдаваться максимум 5 МБ, иначе гугл даже по прямой ссылке отдает html где говорит, что файл мб с вирусом так как больше 5мб не проверяет.

## Build Setup

``` bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn run dev

# build for production and launch server
$ yarn run build
$ yarn start

# generate static project
$ yarn run generate
```

For detailed explanation on how things work, checkout [Nuxt.js docs](https://nuxtjs.org).


