# Тестовое задание на позицию frontend-разработчика в Scentbird

- Необходимо выполнить задание используя заготовку, доступную по ссылке: [frontend-test](https://github.com/scentbird/frontend-test)

- Ссылку на репозиторий с выполненным заданием прислать на andrei@scentbird.com


## Инициализация

- Установите необходимую версию nodejs (nvm или asdf)

- Установка пакетов `npm install`

- Запуск приложения для разработки `npm start`

- Запуск приложения для продакшен сборки `npm run build`

- Доступ к приложению в браузере `http://localhost:8080`


## Общее

1. Задание заключается в реализации SPA-приложение на React на TypeScript.

1. Использование типов **обязательно** для всех компонентов.

1. Обязательно использовать react-router для роутинга.

1. Для стилей SCSS (LESS, POSTCSS) с использованием css modules.

1. Для работы с формой можно использовать любую библиотеку (formik, formular).

1. В описании ниже помимо основных задач есть дополнительные задания, далее (ДОП). Их выполнение не обязательно, но будет плюсом, если вы их выполните.

1. Желательно использовать современные фичи языка.

1. Если возникают вопросы по заданию - не стесняйтесь задавайте.


## Задание

В апп должен быть роутинг для навигации по страницам `/product/:id`, `/checkout`.

В дизайне `design/App.sketch` не представлена навигация по страницам - сделайте в шапке ссылки на эти страницы в любом виде на свое усмотрение. У ссылок должен быть дефолтный стиль и активный.

### Страница товара

1. Страница состоит из двух колонок (desktop, tablet landscape): слева колонка с картинкой / справа колонка с информацией о товаре. Эти колонки должны быть резиновыми (ширина в %).

1. При выборе объема товара (1.7oz Subscription) должна изменяться информация в блоке выбранного товара (выше).

1. При клике на “Read more >” надпись должна заменяться на “< Show less” и раскрывать текст (текст можно использовать любой).

1. (ДОП) Обратить внимание на поведение кнопки “Add to queue” на разных экранах: если она помещается в один ряд с блоком “выбранный товар“, то она должна быть на одном уровне с ним, в противном случае переноситься на новую строку и занимать всю ширину экрана.

1. (ДОП) на мобильной версии обратить внимание на “1.7 oz One-time”, там скрыто слово “purchase”. Придумать решение как скрывать его, в противном случае можно везде писать без этого слова.

### Страница формы

1. Чекбокс *“Use this address…”* должен в отжатом состоянии отображать ниже такую же форму как (выше) *Shipping address*, за исключением поля *“Telephone”*. Заголовок у этой формы должен быть *“Billing address”*.

1. Добавить валидацию в форму: в полях First Name, Last Name можно использовать только буквенные символы. В Street address - числа, пробелы, тире, буквы. Все поля кроме Apt/Suite должны быть required.

1. При сабмите в консоль должна выводиться объект с данными о полях.

1. (ДОП) Можно использовать нативные селекты в форме, но будет плюсом написание своего компонента выпадающего списка.

1. (ДОП) Кнопка Back должна вести на страницу с которой был сделан переход.


### Инфраструктура

1. (ДОП) Сделать экспорт стилей в отдельный файл для production сборки

2. (ДОП) Использовать реальные данные для страницы продукта из публичного graphql.

Endpoint: `https://api.scentbird.com/graphql`

Пример запроса продукта:
```graphql
query Product {
  product(input: { slug: "1000"}) {
    data {
      id
      name
      brandInfo {
        name
      }
      image(fullSizeImage: true)
      rating {
        avgRate
      }
      reviews {
        count
      }
      description
      descriptionSections {
       	id
        title
        ...on TextProductDescriptionSection {
          text
        }
      }
    }
  }
}

```
