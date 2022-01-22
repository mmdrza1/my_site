<template>
  <div class="landing full-width full-height d-flex align-center">
    <v-row>
      <v-col cols="8" offset="2"
        ><div class="full-width d-flex flex-row justify-space-between" :class="">
          <vue-typer
            initial-action="typing"
            type-delay="300"
            :repeat="0"
            text="Hello World!"
            class="font-100"
            @completed="cahnge"
          ></vue-typer>
          <div v-show="myInfo" class="information">
            <p>
              I’m a front-end developer. I’ve got one year of experience in
              front-end programming of web application. I’m mostly Interested in
              learning new technology and use them in my project and also work
              with team and Communicate with people
            </p>
            <div class="d-flex flex-row justify-space-between">
              <v-btn><a href="~/static/CV.pdf" download>CV</a></v-btn>
              <v-btn>contact</v-btn>
            </div>
          </div>
        </div></v-col
      >
    </v-row>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "nuxt-property-decorator";
//@ts-ignore
import { VueTyper } from "vue-typer";
@Component({
  components: { VueTyper },
  filters: {},
})
export default class Default extends Vue {
  [x: string]: any;

  //*variables
  private myInfo: boolean = false;

  private route(link: string) {
    this.$router.push({ name: link });
  }

  private cahnge() {
    this.myInfo = true;
  }
}
</script>

<style lang="scss">
.landing {
  background-image: url("~/static/landing-background.jpg");
  .information {
    color: white;
    width: 40%;
    text-align: justify;
    font-size: 20px;
    animation: information ease 5s;
    -webkit-animation: information ease 5s;
    -moz-animation: information ease 5s;
    -o-animation: information ease 5s;
    -ms-animation: information ease 5s;
  }

  @keyframes information {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }

  @-moz-keyframes information {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }

  @-webkit-keyframes information {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }

  @-o-keyframes information {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }

  @-ms-keyframes information {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }
}
</style>
