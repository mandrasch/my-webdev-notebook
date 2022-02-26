---
title: SvelteKit & Laravel Lighthouse (GraphQL)
created: '2022-01-28T00:12:18.920Z'
modified: '2022-02-04T18:50:37.197Z'
---

# SvelteKit & Laravel Lighthouse (GraphQL)

## Pomodoros 🍅

- 28.01.2022 🍅🍅
- 04.01.2022 🍅🍅🍅

## Tutorial / repos

- Tutorial: **Laracasts: GraphQL with Laravel and Vue** (https://laracasts.com/series/graphql-with-laravel-and-vue)
- Backend repo: https://github.com/mandrasch/greenrunners-laravel-lighthouse-backend
    - GraphQL playground: https://greenrunners-laravel-lighthouse-backend.ddev.site/graphql-playground

## First steps

- Backend repo: https://github.com/mandrasch/greenrunners-laravel-lighthouse-backend
- We only change routes.php later, the rest is laravel
- `ddev artisan make:model News -a`

add to database migration: 

  ```
$table->foreignId('user_id')->constrained();
$table->string('title');
$table->text('body');
  ```
TODO: Why `constrained()`?

add to model user:

  ```
    public function news(){
        return $this->hasMany(News::class);
    }
  ```

add to model news:

  ```
  protected $guarded = [];

    public function user()
    {
        return $this->belongsTo(News::class);
    }
  ```

- further things (factory & seeding), afterwards: `ddev  artisan migrate:fresh --seed` ([Docs](https://laravel.com/docs/8.x/seeding#running-seeders))
- `ddev sequelace`, check created entries

- Install via composer https://lighthouse-php.com/5/getting-started/installation.html#install-via-composer (lighthouse, graphql playground, publish schema)

### Add to app/graphql/schema.graphql

```

"Account of a person who utilizes this application."
type User {
    "Unique primary key."
    id: ID!

    "Non-unique name."
    name: String!

    "Unique email address."
    email: String!

    "When the email was verified."
    email_verified_at: DateTime

    news: [News!]! @hasMany

    "When the account was created."
    created_at: DateTime!

    "When the account was last updated."
    updated_at: DateTime!
}

type News {
    id: ID!
    title: String!
    body: String!
    user: User! @belongsTo
    created_at: DateTime!
    updated_at: DateTime!
}
```

- This approach will have heavy use of [Directives](https://lighthouse-php.com/5/api-reference/directives.html)

This can be queried via

```
query{
  user(id:2){
    name
    news{
      title
    }
  }
}
```

### Pagination


```
query {
  news(page:2) {
    paginatorInfo {
      total
      count
    	currentPage
    }
  }
}
```

### TODOS

- [ ] How to secure graphQL api from outside access?
- [ ] How to do pagination?
<hr>

### GraphQL introduction / Why GraphQL?

- laravel is robust (& secure for multi user web apps?)
- lots of community resources
- there are cost efficient methods of deploying PHP + db (instead of using render.com)
- GraphQL has some advantages (https://www.youtube.com/watch?v=o5orx68OJMg) over REST regarding web apps
    - One request for multiple data objects, https://docs.github.com/en/graphql/overview/explorer
- Most work will be done in the graphql schema

```
query { 
  viewer { 
    avatarUrl
    bioHTML
    followers(first: 5){
      edges{
        node{
          name
        }
      }
    }
    repositories(last: 5){
      edges{
        node{
          name
          url
        }
      }
    }
  }
}
```
- GraphiQL: Shift + Space für Autocomplete
- Public APIs: https://apis.guru/graphql-apis/
- General advice on GraphQL: https://twitter.com/RamboVivaldi/status/1478485106713141252 

