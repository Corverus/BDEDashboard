<template>
  <v-simple-table dark>
    <template v-slot:default>
      <thead>
      <tr>
        <th class="text-left">
          Name
        </th>
        <th class="text-left">
          Id
        </th>
        <th class="text-left">
          Status
        </th>
        <th class="text-left">
          User
        </th>
        <th class="text-left">
          Branch
        </th>
      </tr>
      </thead>
      <tbody>
      <tr
          v-for="item in projects"
          :key="item.id"
      >
        <td>{{ item.name }}</td>
        <td>{{ item.id }}</td>
        <td>{{ item.status }}</td>
        <td>{{ item.user }}</td>
        <td>{{ item.branch }}</td>
      </tr>
      </tbody>
      <button @click="getData">Click</button>
    </template>
  </v-simple-table>
</template>

<script>
export default {
  name: 'pipelineTable',
  data() {
    return {
      projects: []
    }
  },
  methods: {
    getData() {
      const ids = []
      ids.push(23781207)
      for (let x = 0; x < ids.length; x++) {
        const axios = require('axios');
        axios.get(`https://gitlab.com/api/v4/projects/${ids[x]}/pipelines`).then(resp => {
          for (let y = 0; y < resp.data.length; y++) {
            axios.get(`https://gitlab.com/api/v4/projects/${ids[x]}/pipelines/${resp.data[y].id}`).then(res => {
              console.log(res.data)
              this.projects.push(
                  {
                    name: 'Project'+ y,
                    id: res.data.id,
                    status: res.data.status,
                    user: res.data.user.name,
                    branch: res.data.ref
                  }
              )
            })
          }
        })
      }
    }
  }
}
</script>
