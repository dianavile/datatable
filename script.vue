export default {
    data() {
      return {

        config: {
        table_class: 'table table-hover',
        head_class: 'bg-primary', 
        body_class: 'well'
      },

        header: [
          {
            "title": "id",
            "key": "id"
          },
          {
            "title": "title",
            "key": "title"
          },
          {
            "title": "category name",
            "key": "category"
          },
          {
            "title": "create at ...",
            "key": "create"
          },
          {
            "title": "by",
            "key": "author"
          }
        ],
        data: [
          {
            "id": 1,
            "title": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
            "category": "Internet",
            "create": "2017-02-03",
            "author": "administrator"
          },
          {
            "id": 2,
            "title": "Sed hendrerit ex quis erat commodo condimentum.",
            "category": "Cooking",
            "create": "2017-09-15",
            "author": "moderator"
          },
          {
            "id": 3,
            "title": "Maecenas egestas ligula et est accumsan suscipit.",
            "category": "Default",
            "create": "2016-11-21",
            "author": "guest"
          }
        ]
      }
    }
  }
