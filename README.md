# ⚙ Прелоадер - экран загрузки ⚙ 

Источник: видео "Как сделать прелоадер? ► CSS/JS" 
https://vkvideo.ru/video-101965347_456276135?entrypoint=list_all

![2025-01-05_22-07-37](https://github.com/user-attachments/assets/8b4b0054-0c7d-4614-bb7d-784c700b2ec5)


https://github.com/user-attachments/assets/0275f0a4-bcb4-47f0-bc94-4f0029f05b6b



1. создаем создаем файлы index.html, style.css (в папке css), script.js (в папке js) в папке проекта.
   Скачиваем готовые шаблоны изображений (в папку img) и файл js (положить в папку js) и вставляем в папку проекта:


2. в файле index.html готовим шаблон

```html
<!-- Сообщаем браузеру, как стоит обрабатывать эту страницу -->
<!DOCTYPE html>
<!-- Оболочка документа, указываем язык содержимого -->
<html lang="ru">
<!-- Заголовок страницы, контейнер для других важных данных (не отображается) -->
<head>
    <!-- Заголовок страницы в браузере -->
    <title></title>
    <!-- Подключаем CSS -->
    <link rel="stylesheet" href="css/style.css">
    <!-- Кодировка страницы -->
    <meta charset="utf-8">
    <!-- Адаптив -->
    <meta name="viewport" content="width=device-width">
</head>
<!-- Отображаемое тело страницы -->
<body>
<!-- Оболочка для демонстрации -->
<div class="wrapper">
    <!-- Контент -->

    <!-- Подключаем jQuery -->
    <script src="https://code.jquery.com/jquery-3.4.1.min.js"></script>
    <!-- Подключаем файл JS скриптов -->
    <script src="js/script.js"></script>
</div>
</body>
</html>
```

3. в файле style.css вставляем шаблон

```css
/* Обнуление */
*,*:before,*:after{
   padding: 0;
   margin: 0;
   border: 0;
   box-sizing: border-box;
}
/* Стили для демонстрации */
html,body{
   height: 100%;
   background-color: #333;
   font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
   color: #fff;
   font-size: 25px;
}
.wrapper{
   height: 100%;
   padding: 50px;
}
/* Основные стили */
```

4. в файл script.js без шаблона

```js

```

5. в файле index.html вставляем название проекта

```html
<title>Прелоадер</title>
```

6. в файле index.html добавляем классы для прелоадера

```html
<div class="preloader">
    <div class="loader"></div>
</div>
```

7. в файле style.css стилизуем прелоадер

```css
.preloader{
    position: fixed; /* Чтобы окно загрузки распологалось в зависимости от страницы, а не от элементов на странице */
    left: 0;
    top: 0;
    width: 100%; /* Чтобы окно загрузки занимало всю ширину и высоту нашего окна */
    height: 100%;
    background: black;
    z-index: 3; /* Чтобы не было видно наших элементов. Можно повысить z-index, если не перекрывает элементы */

    .loader{ /* Будет простая анимация, пока страница не загрузится */
        width: 75px;
        height: 75px;
        border: 10px solid #fff;
        border-radius: 50%; /* Круглой формоы */
        border-top-color: blue;
        position: absolute; /* Разместить по центру прелоадер */
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
    }
}
```

![7](https://github.com/user-attachments/assets/897ebec0-b100-4262-9352-90e357c7d6bd)


8. в файле style.css создаем анимацию прелоадера

```css
@keyframes spin {
    from {
        transform: translate(-50%, -50%) rotate(0deg);
    }
    to {
        transform: translate(-50%, -50%) rotate(360deg);
    }
}
```
и добавляем строку с анимацией в стилизованный ранее класс .loader
```css
animation: spin 2s linear infinite;
/* Анимация: название spin, время анимации 2 секунды (если меньше - ускорится анимация) */
/* infinite - количество воспроизведений, linear - тайм-функция */
```
и добавляем строку с анимацией в стилизованный ранее класс .preloader
```css
transition: 1s all; /* 1 секунда на все свойства */
opacity: 1;
visibility: visible;
``` 
создаем класс в уже созданном классе .preloader
```css
&.done{  /* Чтобы при загрузке страницы, гифка с прелоадером исчезла */
   opacity: 0;
   visibility: hidden;
}
```



https://github.com/user-attachments/assets/dcf890c4-5e19-4b75-b52d-e130bac2b2e9



9. в файле script.js чтобы прелоадер загружался первым

```js
document.body.onload = function() {
   setTimeout(function() {
      var preloader = document.getElementById('page-preloader');
      // Нужен идентификатор, поэтому в html добавляем его к div preloader
      if (preloader.classList.contains('done')) {
         // Если в preloader в его classList нет класса done, то мы его добавляем
         preloader.classList.add('done');
      }
   }, 1000); // Чтобы грузилось быстрее - 1 секунда
}
```
добавляем идентификатор (id) к preloader в div, чтобы js нашел его
```html
<div id="page-preloader" class="preloader">
   <div class="loader"></div>
</div>
```

10. в файле script.js чтобы прелоадер загружался первым

```js
document.body.onload = function() {
   setTimeout(function() {
      var preloader = document.getElementById('page-preloader');
      // Нужен идентификатор, поэтому в html добавляем его к div preloader
      if (preloader.classList.contains('done')) {
         // Если в preloader в его classList нет класса done, то мы его добавляем
         preloader.classList.add('done');
      }
   }, 1000); // Чтобы грузилось быстрее - 1 секунда
}
```
добавляем идентификатор (id) к preloader в div, чтобы js нашел его
```html
<div id="page-preloader" class="preloader">
   <div class="loader"></div>
</div>
```

# ПРЕЛОАДЕР ГОТОВ. Дальше делаем его красивее, чтобы отображалась картинка и процент загрузки

11. в файле index.html добавляем span в строку с div класса loader

```html
<span id="load_perc"></span>
```

12. в файле index.html меняем название класса с "preloader" на "preloader-2"

```html
<div id="page-preloader" class="preloader-2">
```

13. в файле style.css стилизуем preloader-2. Гифку скачиваем любую.

```css
.preloader-2{
   position: fixed; /* Чтобы окно загрузки распологалось в зависимости от страницы, а не от элементов на странице */
   left: 0;
   top: 0;
   width: 100%; /* Чтобы окно загрузки занимало всю ширину и высоту нашего окна */
   height: 100%;
   background: black;
   z-index: 3; /* Чтобы не было видно наших элементов. Можно повысить z-index, если не перекрывает элементы */
   transition: 1s all; /* 1 секунда на все свойства */
   opacity: 1;
   visibility: visible;
   background: url("../img/loading.gif") center center no-repeat; /* Чтобы не повторялся и централизовывался */
   background-color: #1E1E1E; /* Фон вокруг гифки */

   .loader{ /* Будет простая анимация, пока страница не загрузится */
      width: 100%; /* ЧТобы влезли 100% */
      height: 75px;
      line-height: 75px;
      text-align: center;
      position: fixed; /* Разместить по центру прелоадер */
      left: 50%;
      top: 35%; /* Можно по центру (50%), но будет перекрывать собой гифку */
      transform: translate(-50%, -50%);
      font-size: 75px; /* Размер шрифта */
   }

   &.done{  /* Чтобы при загрузке страницы, гифка с прелоадером исчезла */
      opacity: 0;
      visibility: hidden;
   }
}
```

14. в файле script.js закомментировать старый код, чтобы не удалять.

15. в файле script.js. Заранее отследить время загрузки картинок на сайте

```js
var
        images = document.images,
        images_total_count = images.length,
        images_loaded_count = 0;
```

16. в файле script.js

```js
var
        images = document.images,
        images_total_count = images.length,
        images_loaded_count = 0,
        preloader = document.getElementById('page-preloader'),
        perc_display = document.getElementById('load_perc');

for (var i = 0; i < images_total_count; i++ ) {
   image_clone = new Image();
   image_clone.onload = image_loaded;
   image_clone.onerror = image_loaded;
   image_clone.src = images[i].src;
}

function image_loaded() { // При загрузке до 100%, окно загрузки исчезнет
   images_loaded_count++;
   perc_display.innerHTML = (( ( 100 / images_total_count ) * images_loaded_count ) << 0) + '%';
   // Чтобы при делении не было дробных чисел

   if( images_loaded_count >= images_total_count ) {
      setTimeout(function() {
         if( !preloader.classList.contains('done')) {
            preloader.classList.add('done');
         }
      }, 1000);
   }
}
```

13. в файле index.html для наглядности прелоадера добавляем любые изображения в раздел body (для них создаем папку img)

```html
<div class="gallery">
   <ul class="images">
      <li><img src="img/1.jpg"></li>
      <li><img src="img/2.jpg"></li>
      <li><img src="img/3.jpg"></li>
      <li><img src="img/4.jpg"></li>
   </ul>
</div>
```

14. Чтобы увидеть корректность работы прелоадера - заходим в DevTools (F12) 
на странице с проектом --> Network --> Throttling --> Slow 4G. Также ставим галочку "disable cache" (отключить кэш).


![14](https://github.com/user-attachments/assets/fac94926-74fd-4f45-90aa-dee0a111af85)


# Итог

1. index.html

```html
<!-- Сообщаем браузеру, как стоит обрабатывать эту страницу -->
<!DOCTYPE html>
<!-- Оболочка документа, указываем язык содержимого -->
<html lang="ru">
<!-- Заголовок страницы, контейнер для других важных данных (не отображается) -->
<head>
   <!-- Заголовок страницы в браузере -->
   <title>Прелоадер</title>
   <!-- Подключаем CSS -->
   <link rel="stylesheet" href="css/style.css">
   <!-- Кодировка страницы -->
   <meta charset="utf-8">
   <!-- Адаптив -->
   <meta name="viewport" content="width=device-width">
</head>
<!-- Отображаемое тело страницы -->
<body>
<!-- Оболочка для демонстрации -->
<div class="wrapper">
   <!-- Контент -->
   <div id="page-preloader" class="preloader-2">
      <div class="loader"><span id="load_perc">0%</span></div>
   </div>
   <div class="gallery">
      <ul class="images">
         <li><img src="img/1.jpg"></li>
         <li><img src="img/2.jpg"></li>
         <li><img src="img/3.jpg"></li>
         <li><img src="img/4.jpg"></li>
      </ul>
   </div>
   <!-- Подключаем jQuery -->
   <script src="https://code.jquery.com/jquery-3.4.1.min.js"></script>
   <!-- Подключаем файл JS скриптов -->
   <script src="js/script.js"></script>
</div>
</body>
</html>
```

![2025-01-05_22-14-38](https://github.com/user-attachments/assets/4be6f02f-9d41-47c2-9c59-9ceb9b2f5de6)


2. script.js

```js
//document.body.onload = function() {
//    setTimeout(function() {
//        var preloader = document.getElementById('page-preloader');
//        // Нужен идентификатор, поэтому в html добавляем его к div preloader
//        if (preloader.classList.contains('done')) {
//            // Если в preloader в его classList нет класса done, то мы его добавляем
//            preloader.classList.add('done');
//        }
//    }, 1000); // Чтобы грузилось быстрее - 1 секунда
//}

var
        images = document.images,
        images_total_count = images.length,
        images_loaded_count = 0,
        preloader = document.getElementById('page-preloader'),
        perc_display = document.getElementById('load_perc');

for (var i = 0; i < images_total_count; i++ ) {
   image_clone = new Image();
   image_clone.onload = image_loaded;
   image_clone.onerror = image_loaded;
   image_clone.src = images[i].src;
}

function image_loaded() { // При загрузке до 100%, окно загрузки исчезнет
   images_loaded_count++;
   perc_display.innerHTML = (( ( 100 / images_total_count ) * images_loaded_count ) << 0) + '%';
   // Чтобы при делении не было дробных чисел

   if( images_loaded_count >= images_total_count ) {
      setTimeout(function() {
         if( !preloader.classList.contains('done')) {
            preloader.classList.add('done');
         }
      }, 1000);
   }
}
```

![2025-01-05_22-15-29](https://github.com/user-attachments/assets/234d32a3-906b-4361-a35d-b9ef2e7441a6)


3. style.css

```css
/* Обнуление */
*,*:before,*:after{
   padding: 0;
   margin: 0;
   border: 0;
   box-sizing: border-box;
}
/* Стили для демонстрации */
html,body{
   height: 100%;
   background-color: #333;
   font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
   color: #fff;
   font-size: 25px;
}
.wrapper{
   height: 100%;
   padding: 50px;
}
/* Основные стили */

.preloader-2{
   position: fixed; /* Чтобы окно загрузки распологалось в зависимости от страницы, а не от элементов на странице */
   left: 0;
   top: 0;
   width: 100%; /* Чтобы окно загрузки занимало всю ширину и высоту нашего окна */
   height: 100%;
   background: black;
   z-index: 3; /* Чтобы не было видно наших элементов. Можно повысить z-index, если не перекрывает элементы */
   transition: 1s all; /* 1 секунда на все свойства */
   opacity: 1;
   visibility: visible;
   background: url("../img/loading.gif") center center no-repeat; /* Чтобы не повторялся и централизовывался */
   background-color: #1E1E1E; /* Фон вокруг гифки */

   .loader{ /* Будет простая анимация, пока страница не загрузится */
      width: 100%; /* ЧТобы влезли 100% */
      height: 75px;
      line-height: 75px;
      text-align: center;
      position: absolute; /* Разместить по центру прелоадер */
      left: 50%;
      top: 35%; /* Можно по центру (50%), но будет перекрывать собой гифку */
      transform: translate(-50%, -50%);
      font-size: 75px; /* Размер шрифта */
   }

   &.done{  /* Чтобы при загрузке страницы, гифка с прелоадером исчезла */
      opacity: 0;
      visibility: hidden;
   }
}

.preloader{
   position: fixed; /* Чтобы окно загрузки распологалось в зависимости от страницы, а не от элементов на странице */
   left: 0;
   top: 0;
   width: 100%; /* Чтобы окно загрузки занимало всю ширину и высоту нашего окна */
   height: 100%;
   background: black;
   z-index: 3; /* Чтобы не было видно наших элементов. Можно повысить z-index, если не перекрывает элементы */
   transition: 1s all; /* 1 секунда на все свойства */
   opacity: 1;
   visibility: visible;

   .loader{ /* Будет простая анимация, пока страница не загрузится */
      width: 75px;
      height: 75px;
      border: 10px solid #fff;
      border-radius: 50%; /* Круглой формоы */
      border-top-color: blue;
      position: absolute; /* Разместить по центру прелоадер */
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
      animation: spin 2s linear infinite;
      /* Анимация: название spin, время анимации 2 секунды (если меньше - ускорится анимация) */
      /* infinite - количество воспроизведений, linear - тайм-функция */
   }

   &.done{  /* Чтобы при загрузке страницы, гифка с прелоадером исчезла */
      opacity: 0;
      visibility: hidden;
   }
}

@keyframes spin {
   from {
      transform: translate(-50%, -50%) rotate(0deg);
   }
   to {
      transform: translate(-50%, -50%) rotate(360deg);
   }
}
```

![2025-01-05_22-15-09](https://github.com/user-attachments/assets/570e10f7-c843-430f-a3b1-9733aa0fec63)
![2025-01-05_22-14-54](https://github.com/user-attachments/assets/ef5f0870-c7c8-4640-ab47-ab7251407670)

