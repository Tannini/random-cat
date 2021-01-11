<template>
  <div class="content">
    <h1 style="font">{{ msg }}</h1>
    <form @submit.prevent="getCat">
      <div class="form__input-container">
        <div class="row form-input">
          <div class="col-6 d-flex flex-column align-items-end">
            <label for="text" >Título:</label>
            <label for="text" >Filtro:</label>
            <label for="text" >Color:</label>
            <label for="text" >Tamaño:</label>
          </div>

          <div class="col-6 d-flex flex-column align-items-start">
            <input type="text" class="styleCat" v-model="title"/>
            <select v-model="filter" name="" id="filterCat" class="styleCat">
              <option disabled value="">Cuchifiltro...</option>
              <option value="blur">Blur</option>
              <option value="mono">Mono</option>
              <option value="sepia">Sepia</option>
              <option value="negative">Negative</option>
              <option value="paint">Paint</option>
              <option value="pixel">Pixel</option>
            </select>
          
          <div class="d-flex">
            <select v-model="color" name="" id="colorText" class="styleCat">
              <option disabled value="">Color cuchitexto...</option>
              <option value="red">Rojo</option>
              <option value="blue">Azul</option>
              <option value="green">Verde</option>
              <option value="white">Blanco</option>
              <option value="yellow">Amarillo</option>
            </select>
            
            <div class="circle" :style="{'background-color':color}"></div>
          </div>
          
            <input v-model.number="size" type="number" class="styleCat" />
          </div>
        </div>
      </div>
      
      <input class="btn" type="submit" value="Quiero mi gato!">       
    </form>
    <div class="spinner-border" :class="{ 'd-none': !loading }" role="status">
      <span class="sr-only">Cargando...</span>
    </div>

    <img :src="image">
  </div>
</template>

<script>
export default {
  name: 'RandomCat',
  props: {
    msg: String
  },

  data(){
    return {
      title:"",
      filter:"",
      color:"",
      size:0,
      image:"",
      loading: false,
    };
  },

  methods: {
    getCat() {
      this.loading = true;
      fetch(`https://cataas.com/cat/gif/says/${this.title}?filter=${this.filter}&color=${this.color}&size=${this.size}`)
        .then((data) => {
          this.image = data.url;
          this.loading = false;
        })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
form {
  padding-top: 20px;
}

.form__input-container {
  background-color: lightcoral;
  padding: 20px 40px;
  width: 550px;
}

h1 {
  padding-top: 30px;
  font-weight: bold;
}

label {
  margin-bottom: 14px;
}

.styleCat {
  border-radius: 2px;
  border: 0;
  margin-bottom: 15px;
}

.btn {
  margin-top: 20px;
  margin-bottom: 60px;
  padding: 4px 10px;
  width: 150px;
  background-color: gainsboro;
  border: solid 1px gray;
}

.btn:hover {
  background-color: lightsalmon;
  color: white;
}

.circle {
  height: 20px;
  width: 20px;
  border-radius: 50%;
  display: inline-block;
  margin-left: 1em;
}


</style>
