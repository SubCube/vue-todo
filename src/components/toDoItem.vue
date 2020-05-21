<template>
  <div class="wrapper">
      <div class="name">{{name}}</div>
      <span :class="['mark', marked ? 'yel' : '']" @click="$emit('close')"><i class="fa fa-star"></i>Важная</span>
      <span class="done" @click="$emit('done')"><i class="fa fa-check"></i>Выполнено</span>

  </div>
</template>

<script>
export default {
    name: 'toDoItem',
    props: {
        name: {
            type: String
        },
        marked: {
            type: Boolean,
            default: false
        },
        done: {
            type: Boolean,
            default: false
        }
    }

}
</script>

<style lang="scss" scoped>
    .wrapper{
        display: flex;
        justify-content: space-between;
        .name{
            width: 70%;
            text-align: left;
        }
        .mark{
            margin-right: 10px;
            .fa{
                margin-right: 20px;
            }
            &.yel{
                color: orange;
            }
        }
        span{
            display: flex;
            font-size: 26px;
            cursor: pointer;
        }
    }
</style>
