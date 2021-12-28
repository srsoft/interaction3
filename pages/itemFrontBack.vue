<template>
  <div class="container">
    <div class="flipItem">
      <div class="image" :class="{ on: flip }">
        <div class="item front">
          <img src="https://placeimg.com/150/200/animals" alt="img front">
        </div>
        <div class="item back">
          <img src="https://placeimg.com/150/200/people" alt="img back">
        </div>
      </div>
      <button @click="flip = !flip">
        뒤집기 {{ flip }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      flip: false
    }
  }
}
</script>

<style lang="scss" scoped>
  .container {
    padding: 100px;
  }
  .flipItem {
    display: inline-flex;
    flex-direction: column;
    justify-items: center;
    .image {
      width: 150px;
      height: 200px;
      perspective: 500px;
      .item {
        position: absolute;
        width: 150px;
        height: 200px;
        border: 1px solid #828282;
        font-size: 35px;
        backface-visibility: hidden;
        transition: 0.7s;
        &.front {
          transform: rotateY(0deg);
        }
        &.back {
          transform: rotateY(-180deg);
        }
      }
      &.on {
        .item {
          &.front {
            transform: rotateY(180deg);
          }
          &.back {
            transform: rotateY(0deg);
          }
        }
      }
      // &:hover {
      //   .item {
      //     &.front {
      //       transform: rotateY(180deg);
      //     }
      //     &.back {
      //       transform: rotateY(0deg);
      //     }
      //   }
      // }
    }
    button {
      margin: 10px;
    }
  }
</style>
