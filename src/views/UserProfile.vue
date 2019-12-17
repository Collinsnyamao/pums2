<template>
  <v-container
    fill-height
    fluid
    grid-list-xl>
    <v-layout
      justify-center
      wrap
    >
      <v-flex
        xs12
        md6
      >
        <material-card
          color="green"
          title="Project Profile"
          text="Complete your profile"
        >
          <v-form>
            <v-container py-0>
              <v-layout wrap>
                <v-flex
                  xs12
                  md12
                >

                  <v-select
                          v-model="project"
                          :items="items"
                          :rules="[v => !!v || 'Item is required']"
                          label="Item"
                          required
                  ></v-select>
                </v-flex>
                <v-flex
                  xs12
                  md12
                >
                  <v-text-field
                    label="Add Tasks"
                    class="purple-input"
                    v-model="task"
                  />
                </v-flex>
                <v-flex xs12>
                  <v-textarea
                    class="purple-input"
                    label="Task Description"
                    placeholder="Add a description"
                    v-model="description"
                  />
                </v-flex>
                <v-flex
                  xs12
                  text-xs-right
                >
                  <v-btn
                    class="mx-0 font-weight-light"
                    color="success"
                    @click="taskpusher"
                  >
                    Update Task
                  </v-btn>
                </v-flex>
              </v-layout>
            </v-container>
          </v-form>
        </material-card>
      </v-flex>
      <v-flex
        xs12
        md6
      >
        <material-card
                class="v-card"
                title="Tasks"
                text="Current tasks"
        >
          <!--<v-avatar
            slot="offset"
            class="mx-auto d-block"
            size="130"
          >
            <img
              src="https://demos.creative-tim.com/vue-material-dashboard/img/marc.aba54d65.jpg"
            >
          </v-avatar>-->
          <v-card-text class="text-xs-center text-lg-center">
            <v-list>
              <v-list-item
                      v-for="item in items2"
                      :key="item.title"
                      @click=""
              >
                <v-list-tile-content>

                  <v-list-tile-title v-text="item.title" class="text-lg-center text-xl-center"></v-list-tile-title>
                  <v-list-tile-sub-title v-text="item.title" class="text-lg-center text-xl-center"></v-list-tile-sub-title>
                </v-list-tile-content>
                <v-divider></v-divider>
              </v-list-item>
            </v-list>
          </v-card-text>
        </material-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  //
    data: () => ({
      valid: true,
      name: '',
      project: '',
      task: '',
      description: '',
      nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 10) || 'Name must be less than 10 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      select: null,
      items: [
        'Project 1',
        'Project 2',
        'Project 3',
        'Project 4',
      ],
      items2: [
        { title: 'Jason Oner', description: 'https://cdn.vuetifyjs.com/images/lists/1.jpg' }
      ],
      checkbox: false,
      lazy: false,
    }),

    methods: {
      validate () {
        if (this.$refs.form.validate()) {
          this.snackbar = true
        }
      },
      taskpusher(){
        this.items2.push(this.project,this.description);
      },
      reset () {
        this.$refs.form.reset()
      },
      resetValidation () {
        this.$refs.form.resetValidation()
      },
    },
  }
</script>
