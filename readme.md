# Code and magic

* Приложение: [Code and magic](https://Konnichiwaeien.github.io/code-and-magic)
* Разработчик: [Konnichiwaeien](https://github.com/Konnichiwaeien)
* Дизайн: [HTML Academy](https://htmlacademy.ru/)

## Описание

Демо-страница игры-платформера «Код и Магия», на которой можно поиграть в игру, 
а в специальном окне настроить внешний вид игрового персонажа, купить для него артефакты, 
которые помогают в игре и посмотреть на похожих персонажей других игроков.
В ней маг  может ходить, прыгать и стрелять. Причём управление происходит с помощью 
стрелок, шифта и пробела, как на компьютере. Действия, которые может 
осуществлять настоящий маг:
• стрелять фаерболом в случайном направлении (кнопка «шифт»),
• попадать фаерболом в забор и выигрывать,
• подниматься к верхней границе экрана,
• доходить до левого края экрана (стрелка «влево»),
• доходить до правого края экрана (стрелка «вправо»).

## Технические подробности

* Стандарты разработки: HTML5, CSS3, ES18, progressive enhancement, accessibility.
* Вёрстка: .
* Методология: .
* Сетка: .
* Препроцессор: .
* Автоматизация: .
* Графика: .
* Кроссбраузерность: Chrome, Firefox, Opera, Safari, Edge, IE11, etc.
* Фреймворки/сторонние библиотеки: нет.
* Используемые шрифты: веб-шрифты.
* Дополнительные инструменты: eslint.

## Контакты

* Git: https://github.com/Konnichiwaeien
* Mail: Konnichiwaeien@gmail.com


# Workflow

## Базовые команды

    npm i // устанавливает зависимости
    npm start // собирает проект, удаляет старую сборку, запускает сервер и отслеживание файлов
    npm build // собирает проект, удаляет старую сборку
    npm deploy // загружает текущую сборку проекта на gh-pages

## Работа с растровыми спрайтами

По умолчанию, растровые спрайты не собираются, чтобы работать с растровыми иконками нужно:

1. Создать файл `sprite.less` в директории `src/less`
2. Добавить подключение этого файла в файл `src/less/main.less`

        @import "sprite.less";

3. Добавить таск `"sprite"` в список тасков `build` в `gulpfile.js`

        gulp.task("build", gulp.series("clean", "html", "style", "js", "images", *"sprite"*, "spritesvg", "fonts"));

4. Добавить отслеживание файлов для сборки спрайта в список тасков `observer` в `gulpfile.js`

        gulp.task("observer", function() {
          sync.init(configSync);
          gulp.watch(path.watch.html, gulp.series("html"));
          gulp.watch(path.watch.less, gulp.series("style"));
          gulp.watch(path.watch.js, gulp.series("js"));
          gulp.watch(path.watch.img, gulp.series("images"));
          *gulp.watch(path.watch.sprite, gulp.series("sprite"));*
          gulp.watch(path.watch.spritesvg, gulp.series("spritesvg"));
          gulp.watch(path.watch.fonts, gulp.series("fonts"));
        });