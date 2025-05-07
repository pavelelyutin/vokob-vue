<template>
  <li class="news__item">
    <article class="news__card news-card">
      <div class="news-card__image">
        <img
          :src="`https://okob.vrn.ru${news.image_first}`"
          loading="lazy"
          width="310"
          height="150"
          alt="Новогодний концерт ВОКОБ"
        />
      </div>

      <div class="news-card__inner">
        <div class="news-card__content">
          <h3 class="news-card__title">{{ news.title }}</h3>
        </div>

        <div class="news-card__bottom">
          <a class="news-card__link link" href="#" aria-label="Читать новость подробнее"
            >Читать далее</a
          >
          <time class="news-card__date" datetime="1963-11-22">{{ news.date_news }}</time>
        </div>
      </div>
    </article>
  </li>
</template>

<script>
export default {
  props: {
    news: {
      type: Object,
      required: true,
    },
  },
}
</script>

<style lang="scss">
.news {
  &__swiper {
    overflow: hidden;
  }

  &__item {
    height: auto;
    background-color: transparent;
  }
}

.news-card {
  display: flex;
  flex-direction: column;
  height: 100%;
  border: 1px solid var(--light-color);
  border-radius: var(--border-radius-medium);
  overflow: hidden;
  transition: background-color 0.2s ease-in-out;

  &__image {
    height: 170px;
    width: 100%;
    border-radius: var(--border-radius-medium);
    overflow: hidden;

    img {
      height: 100%;
      transition: transform 0.3s ease-in-out;
    }
  }

  &__inner {
    display: flex;
    flex-direction: column;
    flex-grow: 1;
    align-items: flex-start;
    padding: 30px 15px;
  }

  &__content {
    margin-bottom: 30px;
  }

  &__title {
    margin: 0;
    // margin-bottom: 15px;
    font-family: 'Jost', sans-serif;
    text-transform: uppercase;
    transition: color 0.2s ease-in-out;
  }

  &__bottom {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    margin-top: auto;
  }

  &__link {
    &::before {
      content: '';
      position: absolute;
      inset: 0;
    }
  }

  &:hover:not(:focus-visible) {
    background-color: var(--light-color);
    .news-card__title {
      color: var(--primary-color);
    }
  }
}

.slider-navigation {
  position: absolute;
  display: flex;
  gap: 15px;
  bottom: -18px;
  left: 50%;
  padding: 0 15px;
  transform: translateX(-50%);
  background-color: var(--white-color);

  &__btn {
    &:focus-visible {
      outline: none;

      .slider-navigation__icon {
        circle {
          fill: var(--primary-color);
        }

        path {
          fill: var(--white-color);
        }
      }
    }

    &:hover {
      .slider-navigation__icon {
        circle {
          fill: var(--primary-color);
        }

        path {
          fill: var(--white-color);
        }
      }
    }
  }

  &__icon {
    width: 30px;
    height: 30px;
    color: var(--primary-color);

    circle {
      stroke: currentColor;
      fill: var(--white-color);
      transition: fill 0.2s ease-in-out;
    }

    path {
      fill: currentColor;
      transition: fill 0.2s ease-in-out;
    }
  }
}

.swiper-button-disabled {
  opacity: 0.4;
  cursor: default;

  &:focus-visible {
    .slider-navigation__icon {
      circle {
        fill: none;
      }

      path {
        fill: currentColor;
      }
    }
  }

  &:hover {
    .slider-navigation__icon {
      circle {
        fill: none;
      }

      path {
        fill: currentColor;
      }
    }
  }
}

@media (max-width: 576px) {
  .slider-navigation {
    gap: 10px;
  }
}
</style>
