---
layout: post
title:      "ActiveRecord Relational Methods"
date:       2019-03-28 22:43:54 -0400
permalink:  activerecord_relational_methods
---



In this blog post, I’ll go through some key ActiveRecord relational methods. 
The examples will be based on the following models and associations:
* User: has many reviews, has many books through reviews
* Review: belongs to a user, belongs to a book
* Book: has many reviews, has many users through reviews


### #new and #build

#build is an alias for #new. They both initialize a new instance and will set attributes relevant to the scope. They also both return the new instance and they don’t save to the database.

Example:
```
user = User.last  # => #<User id: 4, username: "jane", email: "j@g.c">
user.reviews.new # => #<Review id: nil, content: nil, stars: nil, user_id: 4, book_id: nil>
user.reviews.build # => #<Review id: nil, content: nil, stars: nil, user_id: 4, book_id: nil>
```
**Note how the user_id for the review was set to 4 automatically.**

If we had a review instance and wanted to create the related book, we could not do `@review.book.build`. This is because `@review.book` is nil until a book is defined. In this case the attribute must be prepended with build_ as shown:
`@review.build_book # => #<Book id: nil, title: nil, author: nil>`

### #create and #create!

* #create and #create! also initialize a new instance, but they also try to save the new record in the database. 
* #create will return the new instance - even if it was not saved due to a validation error. 
* #create! will return the new instance if it was saved successfully, otherwise, #create! will return an error. E.g: `ActiveRecord::RecordInvalid: Validation failed: Title can't be blank, Author can't be blank`
* Similar to `@review.build_book`, we can use `@review.create_book` and `@review.create_book!`.

### #find_or_create_by and  #find_or_create_by!

* The database is searched for the first record with the specified attributes.
* If a record is found, it is returned. 
* If a record is not found, a record is created with the specified attributes.
* Since #create (or #create!) is called, an attempt will be made to save the new record to the database.
* The return value will be as described for #create and #create! in the previous section. 

Example: Book was found in database

```
Book.find_or_create_by(title: "Lord of the Rings", author: "JRRT")
  Book Load (0.4ms)  SELECT  "books".* FROM "books" WHERE "books"."title" = ? AND "books"."author" = ? LIMIT ?  [["title", "Lord of the Rings"], ["author", "JRRT"], ["LIMIT", 1]]
 => #<Book id: 3, title: "Lord of the Rings", author: "JRRT"> 
```

Example: Book was not found in database, so it was created

```
> Book.find_or_create_by(title: "BFG", author: "RD")
  Book Load (1.2ms)  SELECT  "books".* FROM "books" WHERE "books"."title" = ? AND "books"."author" = ? LIMIT ?  [["title", "BFG"], ["author", "RD"], ["LIMIT", 1]]
   (0.1ms)  begin transaction
  Book Exists (0.2ms)  SELECT  1 AS one FROM "books" WHERE "books"."title" = ? LIMIT ?  [["title", "BFG"], ["LIMIT", 1]]
  Book Create (22.6ms)  INSERT INTO "books" ("title", "author") VALUES (?, ?)  [["title", "BFG"], ["author", "RD"]]
   (4.1ms)  commit transaction
 => #<Book id: 4, title: "BFG", author: "RD"> 
```

### #find_or_initialize_by

* This works like #find_or_create_by, except that #new is called instead of #create. Thus, the instance won't be persisted/saved.


#### Resources:

* [Active Record Relation](https://api.rubyonrails.org/classes/ActiveRecord/Relation.html)
* [Active Record Associations - Methods Added by belongs_to](https://guides.rubyonrails.org/association_basics.html#methods-added-by-belongs-to)

