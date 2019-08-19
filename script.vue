import {DatePicker} from 'uiv'
import Vue from 'vue'
Vue.directive('focus', { inserted(el) { el.focus() } })
Vue.directive('selected', { inserted(el) { el.select() } })
export default {
  components: {'my-table': require('@/components/vue-simple-table'), DatePicker},
  data() {
    return {
      header: [
        {
          title: 'ID',
          key: 'id',
          class: 'text-center cursor-pointer'
        },
        {
          title: 'Title',
          key: 'title',
          class: 'cursor-pointer'
        },
        {
          title: 'Category',
          key: 'category',
          class: 'cursor-pointer'
        },
        {
          title: 'Create At',
          key: 'create',
          class: 'text-center cursor-pointer'
        },
        {
          title: 'Author',
          key: 'author',
          class: 'cursor-pointer'
        }
      ],

      body: [{
          class: 'text-center'
        },
        {
          method: {
            dblclick: 'edit',
            slot: 'textarea'
          }
        },
        {
          method: {
            dblclick: 'edit',
            slot: 'select'
          }
        },
        {
          class: 'text-center',
          method: {
            dblclick: 'edit',
            slot: 'calendar'
          }
        },
        {
          method: {
            dblclick: 'edit',
            slot: 'input'
          }
        }
      ],

      data: [
        {
          id: 1,
          title: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
          category: 'Internet',
          create: '2017-02-03',
          author: 'administrator'
        },
        {
          id: 2,
          title: 'Sed hendrerit ex quis erat commodo condimentum.',
          category: 'Cooking',
          create: '2017-09-15',
          author: 'moderator'
        },
        {
          id: 3,
          title: 'Maecenas egestas ligula et est accumsan suscipit.',
          category: 'Default',
          create: '2016-11-21',
          author: 'guest'
        }
      ],

      action: {
        edit_value: '',
        checkbox: [],
        edit_row: {
          id: '',
          title: '',
          category: '',
          create: '',
          author: ''
        }
      }
    }
  },

  methods: {
    say(row) {
      alert('Open console and looking for response object!')
      console.log(row);
    },
    edit(value) {
      this.action.edit_value = value;
    },
    submit(res) { 
      if (res.row[res.k] != this.action.edit_value) {
        let after_update = JSON.parse(JSON.stringify(res.row))
        this.$refs.my_table.set_row_undo(after_update, res.c)
        res.row[res.k] = this.action.edit_value
      }
      this.reset_edit()
    },
    reset_edit() {
      this.$refs.my_table.close()
    },
    set_checkbox(item) {
      this.action.checkbox = item
    },
    edit_row(row) {
      for (let k in row) {
        this.action.edit_row[k] = row[k]
      }
    },
    submit_row(row) {
      let after_update = JSON.parse(JSON.stringify(row))
      for (let key in this.action.edit_row) {
        row[key] = this.action.edit_row[key]
      }
      this.$refs.my_table.set_row_undo(after_update)
      this.$refs.my_table.close(true)
    }
  }
