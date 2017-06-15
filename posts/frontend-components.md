# Замечания к верстке

## Блок типа {type}

Содержит несколько элементов: header, body, footer - это не правило, это пример.

```
<div class=”{sectionName}”>
    <!-- Здесь начинается блок -->
    <div class=”{type}”>
        <!-- Элемент header -->
        <div class=”{type}__header”>
            <h1></h1>
        </div>
        <!-- Элемент body -->
        <div class=”{type}__body”>
            <!-- Внутри нет классов это текст из визуального редактора,
                в нем только простые теги -->
            <h2></h2>
            <p></p>
            <ul><li></li></ul>
        </div>
        <div class=”{type}__footer”></div>
    </div>
    <!-- Здесь заканчивается блок -->
</div>
```

## Блок {type}, содержит блоки {childType1}, {childType2}

```
<div class=”{type}”>
    <div class=”{type}__header”></div>
    <div class=”{type}__body”></div>
    <div class=”{type}__children”>
        <!-- Блок типа 1 -->
        <div class=”{childType1}”>
            <div class=”{childType1}__header”></div>
            <div class=”{childType1}__body”></div>
            <div class=”{childType1}__footer”></div>
        </div>
        <!-- Еще блок типа 1 -->
        <div class=”{childType1}”>
            <div class=”{childType1}__header”></div>
            <div class=”{childType1}__body”></div>
            <div class=”{childType1}__footer”></div>
        </div>
        <!-- Блок типа 2 -->
        <div class=”{childType2}”>
            <div class=”{childType2}__header”></div>
            <div class=”{childType2}__body”></div>
            <div class=”{childType2}__footer”></div>
        </div>
    </div>
    <div class=”footer”></div>
</div>
```

## Как не надо

```
<ul class=”menu-header”>
    <li class=”menu-header__item”>
        <a class=”menu-header__link”></a>
    </li>
</ul>

<ul class=”menu-footer”>
    <li class=”menu-footer__item”>
        <a class=”menu-footer__link”></a>
    </li>
</ul>
```

## Надо так

```
<!-- Модификатор _header только у родителя  -->
<ul class=”menu menu_header”>
    <!-- Здесь элемент menu__item вместо menu-header__item -->
    <li class="menu__item">
        <a class="menu__link"></a>
    </li>
    <!-- Добавляется модификатор для активного пункта меню  -->
    <li class=”menu__item menu__item-active”>
        <a href=”#”></a>
    </li>
</ul>

<!-- Модификатор _footer только у родителя  -->
<ul class=”menu menu_footer”>
    <!-- Здесь элемент menu__item вместо menu-footer__item -->
    <li class="menu__item">
        <a class="menu__link"></a>
    </li>
    <!-- Добавляется модификатор для активного пункта меню  -->
    <li class=”menu__item menu__item-active”>
        <a href=”#”></a>
    </li></ul>
```

## Идеальный вариант
С точки зрения бекенд-разработчика - для обсуждения - не прописывать li.class, а задать отображение через menu_header > li

```
<!-- Модификатор _header только у родителя  -->
<ul class=”menu menu_header”>
    <!-- список элементов одинаковый у всех меню -->
    <li>
        <a></a>
    </li>
    <!-- Добавляется модификатор для активного пункта меню  -->
    <li class="active">
        <a href=”#”></a>
    </li>
</ul>

<!-- Модификатор _footer только у родителя  -->
<ul class=”menu menu_footer”>
    <!-- список элементов одинаковый у всех меню -->
    <li>
        <a></a>
    </li>
    <!-- Добавляется модификатор для активного пункта меню  -->
    <li class="active">
        <a href=”#”></a>
    </li>
</ul>
```

## Как не надо

```
<div class="info-box">
    <h3>О проекте</h3>
    <p>
        Данная концепция интерьера салона рассказывает о настроении и философии бренда Londa Professional — фокус на высоком уровне сервиса и интересах клиента. Дизайн и декор салона свежие, яркие и современные, лаконичные и не имеют лишних деталей.
    </p>
    <!-- Откуда взяться br? Это текст из визуального редактора.
        Нужно или правило по форматированию в редакторе.
        Или дополнительное преобразование текста при выводе в шаблоне -->
    <br>
    <p>
        Минимализм — это образ жизни, а не просто дань моде. Яркие нотки дизайну можно придать при помощи насыщенных цветов мебели, ярких хардпостеров на стенах и некоторых элементов брендинга.
    </p>
</div>
```

## Как не надо

```
<div class="main-salon__salon-about">
    <!-- Это текст из визуального редактора целиком
        В нем неуместны атрибуты class -->
    <h1 class="main-salon__title">
        <!-- Регистр должен быть преобразован средствами css -->
        КОНЦЕПЦИЯ СОВРЕМЕННОГО САЛОНА&nbsp;КРАСОТЫ
    </h1>
    <ul class="salon-advantages">
        <!-- Это текст из визуального редактора целиком
            В нем неуместны атрибуты class -->
        <li class="salon-advantages__item">
            Мы создаем уютные интерьеры для салонов красоты, в которые хочется вернуться.
        </li>
        <li class="salon-advantages__item">
            С нами работают 20 000 салонов красоты и индивидуальных парикмахеров по всей стране.
        </li>
        <li class="salon-advantages__item">
            Предлагаем три концепции салона красоты, которые содержат основные элементы бренда.
        </li>
    </ul>
</div>
```

## Как надо

```
<div class="main-salon__salon-about">
    <!-- Особенности отображения h, p, u, li - заданы через main-salon__salon-about -->
    <h1>Концепция современного салона красоты</h1>
    <ul>
        <li>
            Мы создаем уютные интерьеры для салонов красоты, в которые хочется вернуться.
        </li>
        <li>
            С нами работают 20 000 салонов красоты и индивидуальных парикмахеров по всей стране.
        </li>
        <li>
            Предлагаем три концепции салона красоты, которые содержат основные элементы бренда.
        </li>
    </ul>
</div>
```