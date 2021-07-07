<template>
  <div class="about">
    <h1 class="about__heading">Эта страничка о тестовом задании</h1>
    <article class="about__text">
      Нужно написать простой загрузчик картинок. Суть: Есть контейнер, куда
      можно перетаскивать файлы. При перетаскивании, контейнер должен
      посмотреть, что за файл он получает. Если картинка, то превью картинки
      вставляется в контейнер. Рядом лежит кнопка "отправить". При нажатии на
      нее, нужно взять файл, перегнать его в base64 и вывести результат в
      console.log. Файлов можно загрузить несколько. Только картинки должны быть
      выведены в консоль. Требования: - Повторно один и тот же файл добавлять
      нельзя - Не использовать библиотеки/фреймворки для загрузки файлов -
      Использовать Vue.js (желательно 3 версии) - Стилизация на твое усмотрение
    </article>
  </div>
  <router-link to="/" class="about__link"
    >Вернуться на главную страницу</router-link
  >
</template>

<style lang="less" scoped>
.about {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  &__heading {
  }
  &__link {
    font-weight: bold;
    color: #42b983;
    margin: 30px 0;
    text-decoration: none;
  }
  &__text {
    display: flex;
    width: 50%;
    text-align: center;
  }
}
</style>
