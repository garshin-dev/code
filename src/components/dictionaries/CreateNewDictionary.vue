<template>
  <div class="create_block">
    <div class="circle">
      <div class="vertical-line"></div>
      <div class="horizontal-line"></div>
    </div>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped lang="scss">
  .create_block {
    width: 230px;
    height: 300px;
    border: 3px solid #A2ACBF;
    box-sizing: border-box;
    border-radius: 5px;
    margin-left: 60px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    margin-top: 60px;

    &:hover {
      transition: .3s;
      border: 3px solid #47ff47;
      background-color: rgba(71, 255, 71, .2);

      .circle {
        transition: .3s;
        border: 3px solid #47ff47;

        .vertical-line {
          transition: .3s;
          background-color: #47ff47;
        }

        .horizontal-line {
          transition: .3s;
          background-color: #47ff47;
        }
      }
    }

    .circle {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 60px;
      height: 60px;
      border-radius: 100%;
      border: 3px solid #A2ACBF;

      .vertical-line {
        transform: rotate(-90deg);
        width: 20px;
        height: 3px;
        background-color: #A2ACBF;
      }

      .horizontal-line {
        position: absolute;
        transform: rotate(-180deg);
        width: 20px;
        height: 3px;
        background-color: #A2ACBF;
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
    .create_block {
      margin-left: 20px;
      width: 200px;
      height: 280px;
    }
  }

  /* Extra Small Devices, Phones */
  @media only screen and (max-width: 480px) {
    /* */
  }

  /* Custom, iPhone Retina */
  @media only screen and (max-width: 320px) {
    /* */
  }
</style>