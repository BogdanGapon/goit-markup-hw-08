1. # Открытие мобильного меню

   Коварно похищено у https://github.com/Olexiy-repin/fs-on-49-online/blob/module-08/README.md

   Мобильное меню открывается по клику на **кнопку** "бургера". Для того чтобы скрипт сработал
   необходимо добавить в разметку специальные атрибуты, по которым скрипт ищет элементы:

- `data-menu-open` - на кнопку открытия мобильного меню(бургер)
- `data-menu-close` - на кнопку закрытия мобильного меню(крестик)
- `data-menu` - на мобильное меню

После чего, перед закрывающим тегом body добавить тег script со ссылкой на файл скрипта для
мобильного меню.

```html
<body>
  <!-- Ставим перед закрывающим тегом body -->
  <script src="./js/menu.js"></script>
</body>
```

Вот скрипт который необходимо скопировать и вставить в файл скрипта menu.js.

```js
(() => {
  const refs = {
    openMenuBtn: document.querySelector('[data-menu-open]'),
    closeMenuBtn: document.querySelector('[data-menu-close]'),
    menu: document.querySelector('[data-menu]'),
  };

  refs.openMenuBtn.addEventListener('click', toggleModal);
  refs.closeMenuBtn.addEventListener('click', toggleModal);

  function toggleModal() {
    refs.menu.classList.toggle('is-open');
  }
})();
```

Изначально мобильное меню должно быть скрыто, например с помощью:

```css
.mobile-menu {
  opacity: 0;
  visibility: hidden;
  pointer-events: none;
}
```

Мобильное меню открывается когда на него вешается клас `is-open`. Нужно описать еще этот клас,
например:

```css
.mobile-menu.is-open {
  opacity: 1;
  visibility: visible;
  pointer-events: auto;
}
```
 
Как вычитывается размер картинки при дескрипторе ```w```
Нужно размер вьюпора умножить на DPR  и разделить на размер картинки указанный в теге ```img``` в разметке hmtlю 
Например ```размер вьюпорта 600px и DPR = 2, а размер картинки 25vw получается что 1200 / 4 = 300px то есть будет загружена картинка которая ближе всего к данному размеру.```
