<template>
  <div>
    <v-navigation-drawer app fixed v-model="drawer">
      <v-card class="mx-auto" max-width="100%" tile>
        <v-img
          height="100%"
          src="https://i.pinimg.com/564x/f6/dc/ac/f6dcac1d28b4354ff135bca17bdc8df4.jpg"
        >
          <v-row align="end" class="fill-height">
            <v-col align-self="start" class="pa-0" cols="12">
              <v-avatar class="profile" color="grey" size="164" tile>
                <v-img :src="getPhoto()"></v-img>
              </v-avatar>
            </v-col>
            <v-col class="py-0">
              <v-list-item color="rgba(0, 255, 0, 0.3)" dark>
                <v-list-item-content>
                  <v-list-item-title class="title">{{
                    lineprofile.displayName
                  }}</v-list-item-title>
                  <v-list-item-subtitle
                    >{{ lineprofile.statusMessage }}
                  </v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
            </v-col>
          </v-row>
        </v-img>
      </v-card>
      Thanchanok
    </v-navigation-drawer>

    <v-app-bar 
    app 
    fixed 
    dark 
    color="pink accent-1"
    shrink-on-scroll
    prominent
    src="https://i.pinimg.com/564x/c0/e3/47/c0e34758fd701463a5989a4373e816d2.jpg"
    fade-img-on-scroll
    scroll-target="#scrolling-techniques-5"
    scroll-threshold="500"
    >
    <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right,rgba(249, 93, 137, 1),rgba(246, 152, 178, 1)"
        ></v-img>
      </template>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      
      <v-toolbar-title>Ducking Hero</v-toolbar-title>
     <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-app-bar>
  </div>
</template>

<script>
export default {
  name: "TopToolbar",
  data: () => ({
    drawer: null,
    lineprofile: {
      userId: "",
      displayName: "",
      pictureUrl: "https://www.flaticon.com/svg/static/icons/svg/3790/3790767.svg",
      statusMessage: ""
    }
  }),
  mounted() {
    this.$liff.init(
      { liffId: "1655383435-d8jLRLEx" },
      () => {
        if (this.$liff.isLoggedIn()) {
          console.log("isLoggedIn");
        } else {
          this.$liff.login();
        }
        this.getLineProfile();
      },
      err => console.error(err.code)
    );
  },
  methods: {
    getPhoto() {
      return this.lineprofile.pictureUrl;
    },
    getLineProfile() {
      let _this = this;
      this.$liff
        .getProfile()
        .then(function(profile) {
          _this.lineprofile = profile;
          //_this.lineprofile.pictureUrl="\""+_this.lineprofile.pictureUrl+"\""
          //alert(_this.lineprofile.pictureUrl);
        })
        .catch(function(error) {
          alert("Error getting profile: " + error);
        });
    }
  }
};
</script>
