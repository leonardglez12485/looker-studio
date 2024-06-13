<script>
import * as pbi from "powerbi-client";
export default {
  name: 'HelloWorld',

data(){
  return {
  config: {
    type: 'PoweBIReport',
    id: 'b2e382aa-3d54-4eb3-9a0c-d998a39f8f40',
    embedUrl:'https://app.powerbi.com/reportEmbed?reportId=b2e382aa-3d54-4eb3-9a0c-d998a39f8f40&autoAuth=true&ctid=760fe82f-1c6d-4e38-9fa9-994e8f3fcb10',
    permissions: pbi.models.Permissions.READ,
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
      const embedContainer = this.$refs.container;
      // const embedContainer = document.getElementById('container');
      const powerbi = new pbi.service.Service(
        pbi.factories.factories.hpmFactory,
        pbi.factories.factories.wpmpFactory,
        pbi.factories.factories.routerFactory
      );
      const dashboard = powerbi.embed(embedContainer, this.config);
      dashboard.off("loaded");
      dashboard.off("rendered");
      dashboard.on("error", function () {
      this.dashboard.off("error");
   });
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
  <h1>Test Power-BI</h1>
  <div>
   <!-- <section id="container" style="height: 750px"/> -->
   <!-- <section ref="container" style="height: 750px"/> -->
   <iframe src="https://app.powerbi.com/reportEmbed?reportId=d5b2554b-0d31-4e19-a310-c3610edfaaa3&autoAuth=true&ctid=760fe82f-1c6d-4e38-9fa9-994e8f3fcb10" width="100%" height="600px"></iframe>
  </div>
</template>


