<template>
  <div id="app">
    <div class="panel-left">
      <div>
        <input type="checkbox" v-model="setShadow">Disabled shadow
      </div>
      <div>
        <input type="checkbox" v-model="setDisabled">Disabled button
      </div>
      <div>
        <input type="checkbox" v-model="setIconLeft">Icon left
      </div>
      <div>
        <input type="checkbox" v-model="setIconRight">Icon right
      </div>
      <div class="radio">
        <div>
          <input
            type="radio"
            id="sm"
            v-model="buttonSize"
            value="sm"
            checked 
          />Size SM
        </div>
        <div>
          <input
            type="radio"
            id="md"
            v-model="buttonSize"
            value="md" 
          />Size MD
        </div>
        <div>
          <input
            type="radio"
            id="lg"
            v-model="buttonSize"
            value="lg"
          />Size LG
        </div>
      </div>
      <div class="radio">
        <div>
          <input
            type="radio"
            id="default"
            v-model="buttonColor"
            value="default"
            checked 
          />Color default
        </div>
        <div>
          <input
            type="radio"
            id="primary"
            v-model="buttonColor"
            value="primary"
          />Color primary
        </div>
        <div>
          <input
            type="radio"
            id="secondary"
            v-model="buttonColor"
            value="secondary"
          />Color secondary
        </div>
        <div>
          <input
            type="radio"
            id="danger"
            v-model="buttonColor"
            value="danger"
          />Color danger
        </div>
      </div>
    </div>
    <div class="panel-right">
      <div class="container">
        <div class="item">
          <Button
            :disableShadow="setShadow"
            :disabled="setDisabled"
            :startIcon="setIconLeft ? 'add_shopping_cart' : ''"
            :endIcon="setIconRight ? 'add_shopping_cart' : ''"
            :size="buttonSize"
            :color="buttonColor"
          ></Button>
        </div>
        <div class="item">
          <Button
            :disableShadow="setShadow"
            :disabled="setDisabled"
            variant="outline"
            :startIcon="setIconLeft ? 'add_shopping_cart' : ''"
            :endIcon="setIconRight ? 'add_shopping_cart' : ''"
            :size="buttonSize"
            :color="buttonColor"
          ></Button>
        </div>
        <div class="item">
          <Button
            :disableShadow="setShadow"
            :disabled="setDisabled"
            variant="text"
            :startIcon="setIconLeft ? 'add_shopping_cart' : ''"
            :endIcon="setIconRight ? 'add_shopping_cart' : ''"
            :size="buttonSize"
            :color="buttonColor"
          ></Button>
        </div>
      </div>
    </div>
    <footer>Iván Lara Gómez - 2020</footer>
  </div>
</template>

<script>
import Button from "./components/Button.vue";

export default {
  name: "App",
  data() {
    return {
      setShadow: false,
      setDisabled: false,
      setIconLeft: false,
      setIconRight: false,
      buttonSize: '',
      buttonColor: 'default'
    }
  },
  components: {
    Button
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@500&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Material+Icons");
#app {
  font-family: "Noto Sans JP", sans-serif;
  margin: 10px;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: space-between;
  align-content: center;
  align-items: center;
  .container {
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    justify-content: space-between;
    align-content: center;
    align-items: center;
    box-shadow: 0 0 8px 3px rgba(0,0,0,.2);
    margin: 10px 0 30px 0;
    height: 75px;
    .item {
      margin: 10px    
    }
  }
  .panel-left {
    height: calc(100vh - 20px);
    width: 30%;
    padding: 10px;
  }
  .panel-right {
    height: calc(100vh - 20px);
    width: 70%;
    padding: 10px;
  }
  .radio {
    margin-top: 10px;
  }
}
footer {
  position: fixed;
  bottom: 0;
  border-top: 1px solid #dddddd;
  width: 100vw;
  left: 0;
  padding: 10px;
  text-align: center;
}
</style>
