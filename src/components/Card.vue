<template>
    <div class="col-sm-6 col-md-4 col-lg-3">
      <h3>{{card.name}}</h3>
      <img class="img-fluid" :src="card.image" alt="">
      <h4>{{card.species}}</h4>
      <h6>{{card.origin}}</h6>
    </div>
</template>

<script>
export default {
  name: 'Card',
  props:{
    card:Object
  }
}
</script>

<style lang="scss" scoped>
  img{
    margin-bottom: 15px;
    border-radius: 50%;
    box-shadow: 0 5px 5px rgba(0,0,0,.3);
    transition: all .3s;
    &:hover{
      transform: scale(1.05,1.05);
      filter: brightness(115%);
      box-shadow: 0 15px 15px rgba(0,0,0,.3);

    }
  }
  h3{
    min-height: 67px;
  }
</style>