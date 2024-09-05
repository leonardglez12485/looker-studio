<script>
import * as pbi from "powerbi-client";
export default {
  name: 'HelloWorld',

data(){
  return {
  config: {
    type: 'dashboard',
    tokenType: pbi.models.TokenType.Embed,
    accessToken:  "autoAuth=true&ctid=760fe82f-1c6d-4e38-9fa9-994e8f3fcb10",
    id: "b2e382aa-3d54-4eb3-9a0c-d998a39f8f40",
    embedUrl:"https://app.powerbi.com/reportEmbed",
    pageView: 'fitToWidth',
    permissions: pbi.models.Permissions.All,
    settings: {
          filterPaneEnabled: true,
          navContentPaneEnabled: true,
        },
  },
  };
},
mounted() {
    this.embedDashboard();
  },
  methods: {
     embedDashboard() {
    //  const embedContainer = this.$refs.container;
     
      let powerbi = new pbi.service.Service(
        pbi.factories.hpmFactory,
        pbi.factories.wpmpFactory,
        pbi.factories.routerFactory
      );
      const embedContainer = document.getElementById('container');
      const dashboard = powerbi.embed(embedContainer, this.config);
      dashboard.off("loaded");
      dashboard.off("rendered");
      dashboard.on("error", function () {
      this.dashboard.off("error");
  });

  const dashboardRef = powerbi.embed(embedContainer, this.config);
   dashboardRef.off("loaded");
   dashboardRef.off("rendered");
   dashboardRef.on("error", function () {
   this.dashboardRef.off("error");
   });

//    let powerbi = new pbi.service.Service(pbi.factories.hpmFactory, pbi.factories.wpmpFactory, pbi.factories.routerFactory);
//    const dashboardContainer = document.getElementById('container');
//   try {
//     const dashboard = powerbi.embed(dashboardContainer, this.config);
//    dashboard.off("loaded");
//    dashboard.off("rendered");
//    dashboard.on("error", function () {
//      this.dashboard.off("error");
//    });
//   } catch (error) {
//     console.log(error)
//   }

// try {
//   const dashboardRef = powerbi.embed(dashboardContainer, this.config);
//    dashboardRef.off("loaded");
//    dashboardRef.off("rendered");
//    dashboardRef.on("error", function () {
//    this.dashboardRef.off("error");
//    });
// } catch (error) {
//   console.log(error)
// }
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

<template>
  <h1>Test Looker Studio</h1>
  <div class="test-1">
    <h2>Dashboard I</h2>
   <!--<section id="container" style="height: 750px"/>-->
   <!-- <section ref="container" style="height: 750px"/> -->
   <iframe width="1200" height="950" src="https://lookerstudio.google.com/embed/reporting/0f3d48b7-a52a-4542-98a0-a0182ca61514/page/BHP6D" frameborder="0" style="border:0" allowfullscreen sandbox="allow-storage-access-by-user-activation allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox"></iframe>
  </div>

  <div class="test-2">
    <h2>Dashboard II</h2>
    <iframe width="1200" height="950" src="https://lookerstudio.google.com/embed/reporting/0bd48870-462f-412f-b85b-bf9d5577e3d9/page/I4T6D" frameborder="0" style="border:0" allowfullscreen sandbox="allow-storage-access-by-user-activation allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox"></iframe>
  </div>
</template>

<style scoped>
@import '../style.css';
</style>


