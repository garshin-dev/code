<template>
  <div class="text">
    <div class="title">
      <h2>
        <router-link :to="`/text/${id_text}`" :some="245">{{ title }}</router-link>
      </h2>
      <div v-if="publicAccess === '1'" class="public">
        Общий
      </div>
    </div>
    <div class="main">
      <p class="content">
        {{ text }}
      </p>
      <div class="dark"></div>
    </div>
    <div class="buttons">
      <button v-if="deleteTextBool" class="delete" @click="$emit('deleteText', id_user, id_text)">Удалить</button>
      <button v-else class="deleteFake"></button>
      <router-link class="forward" :to="`/text/${id_text}`">Вперед</router-link>
      <button
          class="statistics"
          @click="showModalStatistics = true">
        Статистика
      </button>
    </div>
  </div>

  <teleport to="body">
    <ModalStatistics
      v-if="showModalStatistics"
      :id_text="id_text"
      :publicAccess="publicAccess"
      @closeModalStatistics="showModalStatistics = false"
    />
  </teleport>
</template>

<script>
import ModalStatistics from "@/components/texts/ModalStatistics";

export default {
  emits: ['deleteText'],
  props: ['title', 'text', 'id_user', 'id_text', 'publicAccess', 'deleteTextBool'],
  data() {
    return {
      showModalStatistics: false
    }
  },
  components: {
    ModalStatistics
  }
}
</script>

<style scoped lang="scss">
  .text {
    position: relative;
    box-sizing: border-box;
    box-shadow: 10px 10px 15px -3px #000000;
    margin: 40px auto 0;
    display: flex;
    flex-wrap: nowrap;
    align-content: center;
    justify-content: space-between;
    border-radius: 5px;
    min-height: 170px;
    transition: .3s;
    width: 100%;
    flex-direction: column;

    &:hover {
      //box-shadow: none;
      box-shadow: 5px 5px 15px -3px #000000;
    }

    .title {
      padding: 10px 0;
      position: relative;
      text-align: center;
      background-color: #0DFF92;
      h2 {
        a {
          font-weight: bold;
          font-size: 30px;
          color: #36404A;
        }
      }

      .public {
        position: absolute;
        top: 5px;
        right: 5px;
        border: 2px solid #7521ff;
        font-size: 14px;
        font-weight: bold;
        color: #7521ff;
        padding: 2px 5px;
      }
    }

    .main {
      height: 175px;
      position: relative;
      overflow: hidden;

      .content {
        padding: 5px 0 0 5px;
        font-size: 23px;
        color: #FFFFFF;
        max-height: 170px;
        overflow: hidden;
      }

      .dark {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(to top, black 0%, rgba(0, 0, 0, 0.7) 100%);
      }
    }

    .buttons {
      position: absolute;
      bottom: 0;
      left: 0;
      display: flex;
      justify-content: space-between;
      align-items: center;
      width: 100%;
      z-index: 5;
      padding: 0 0 10px;

      .deleteFake {
        border: 2px solid transparent;
        margin-left: 70px;
        font-weight: bold;
        font-size: 14px;
        background: transparent;
        padding: 5px 10px;
        border-radius: 3px;
      }

      button.delete, a.forward, button.statistics {
        font-weight: bold;
        font-size: 14px;
        background: transparent;
        padding: 5px 10px;
        border-radius: 3px;
        cursor: pointer;
        transition: .3s;

        &:hover {
          color: #fff;
        }
      }

      button.delete {
        border: 2px solid #FF4D4D;
        color: #FF4D4D;
        margin-left: 10px;

        &:hover {
          background-color: #FF4D4D;
          box-shadow: 0 0 20px 3px #FF4D4D;
        }
      }

      a.forward {
        color: #06bb0c;
        border: 2px solid #06bb0c;

        &:hover {
          background-color: #06bb0c;
          box-shadow: 0 0 20px 3px #06bb0c;
        }
      }

      button.statistics {
        color: #363EFF;
        border: 2px solid #363EFF;
        margin-right: 10px;

        &:hover {
          background-color: #363EFF;
          box-shadow: 0 0 20px 3px #363EFF;
        }
      }
    }
  }

  /* Large Devices, Wide Screens */
  @media only screen and (max-width: 1200px) {
    /* */
  }

  /* Medium Devices, Desktops */
  @media only screen and (max-width: 992px) {
    /* */
  }

  /* Small Devices, Tablets */
  @media only screen and (max-width: 768px) {
    /* */
  }

  /* Extra Small Devices, Phones */
  @media only screen and (max-width: 480px) {
    .text {
      .title {
        h2 {
          a {
            font-size: 24px;
          }
        }
      }

      .main {
        .content {
          padding: 5px 0 0 5px;
          font-size: 18px;
          color: #FFFFFF;
          max-height: 170px;
        }
      }

      .buttons {
        button.delete, a.forward, button.statistics {
          font-size: 12px;
          padding: 5px 10px;
        }
      }
    }
  }

  /* Custom, iPhone Retina */
  @media only screen and (max-width: 320px) {
    /* */
  }
</style>