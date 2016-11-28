# Rails API Relationships Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  Describe a reason why a join tables may be valuable.

```sh
  to add things to already created table.
```

1.  Provide a database table structure and explain the Entity Relationship that
describes a many-to-many relationship for `Profiles`, `Movies` and `Favorites`
(Think of Netflix). A `Profile` has a `given_name`, `surname` and `email` and a
`Movies` have `title`, `release_date`, and `length` and `Favorites` would be the
join table with references to `Movies` and `Profiles`.

```sh
  |profile| ---- |favorites| -----|Movies|

  not really sure what this is asking as it seems to be answering it in the second
  sentence. Profile and Movies are connected through Favorites. Each table have their own
  attributes.
```

1.  For the above example, what needs to be added to the Model files?

```rb
class Profile < ActiveRecord::Base
  def change
    create_table :profiles do |t|
    t.string :given_name
    t.string :surname
    t.string :email
end
```

```rb
class Movie < ActiveRecord::Base
  def change
    create_table :movies do |t|
    t.string :title
    t.string :release_date
    t.string :length
end
```

```rb
class Favorite < ActiveRecord::Base
  def change
    create_join_table :movies, :profiles
end
```

1.  What is the purpose of a serializer? What would our `Profile` serializer look
like to show all movies favorited by a profile on
`http://localhost:3000/profiles/1`

```sh
  it helps to organize which relationships should be organized.
```

```rb
class ProfileSerializer < ActiveModel::Serializer
end
```

1.  What would the command be to _scaffold_ out a **join table** for Favorites from
the above `Movies` and `Profiles`.

```sh
  rails g scaffold favorites
```

1.  What is `Dependent: Destroy` and where/why would we use it?

```sh
  to destroy a table when it is in a dependant relationship. to destroy a table if they
  are connected.
```

1.  Think of **ANY** example where you would have a one-to-many relationship as well
as a many-to-many relationship in an application. You only need to list the
description about the resources and how they relate to one another.

```sh
  quotes to author. a quote would have an author, an author will have a quote.
  However , a single author can have many quotes. 
```
