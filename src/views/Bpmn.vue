<template>
  <div>
    <bpmn-modeler
        ref="refNode"
        :xml="xml"
        :users="users"
        :groups="groups"
        :categorys="categorys"
        :is-view="false"
        @save="save"
    />
  </div>
</template>

<script>
import bpmnModeler from "workflow-bpmn-modeler";
import axios from "axios";

export default {
  components: {
    bpmnModeler,
  },
  data() {
    return {
      xml: "", // 后端查询到的xml
      users: [
        { name: "javaboy", id: 1 },
        { name: "itboyhub", id: 2 },
        { name: "江南一点雨", id: 3 },
      ],
      groups: [
        { name: "经理", id: 4 },
        { name: "组长", id: 5 },
        { name: "员工", id: 6 },
      ],
      categorys: [
        { name: "OA", id: "oa" },
        { name: "财务", id: "finance" },
      ],
    };
  },
  methods: {
    save(data) {
      console.log(data); // { process: {...}, xml: '...', svg: '...' }
    },
  },
  mounted() {
    axios
        .get(
            "https://cdn.jsdelivr.net/gh/goldsubmarine/workflow-bpmn-modeler@master/src/Leave.bpmn20.xml"
        )
        .then((response) => {
          this.xml = response.data;
        })
        .catch((error) => {
          console.log(error);
        });
  },
};
</script>
