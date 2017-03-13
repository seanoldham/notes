My web development notes, snippets, and whatnot.

[Ruby](ruby/hash.md)
=====

Ruby on Rails
=====

### Params

Let's say we have two models, `Collection` and `Product`. A `Collection` can have many `Products` and a `Product` can be in many `Collections`. Let's also say that when creating a new `Product`, we already know which `Collections` we want it to be in. We'll want to whitelist the `collection_ids` param in the `products_controller` so we can pass that info when we create our `Product`. Since there could be multiple `Collections` passed, we'll want to write it like this: `params.require(:product).permit(:all, :the, :other, :params, collection_ids: [])`. This allows an array of `Collections` to be passed instead of a single value.

[Searchkick](http://searchkick.org)
-----

### Partial Match

Can do [partial matches](https://github.com/ankane/searchkick#partial-matches). I followed the README and added this to my Drawing model:
```ruby
searchkick  text_end: [:number], text_middle: [:number]
```
However, when I went to make it run, after `Drawing.reindex` of course, instead of doing
```ruby
Drawing.search(params[:term], limit: 30, fields: [:number], match: [:text_end, :text_middle])
```
I had to squish them together like
```ruby
Drawing.search(params[:term], limit: 30, fields: [{number: :text_end, number: :text_middle}])
```

Command Line
=====

### Open Directory in Finder

I feel dumb for having to write this one up, but all it takes is `open .` for the current directory.


[Hotel](https://github.com/typicode/hotel)
-----

### Adding a Rails project

When in the project folder, just do
```
hotel add 'rails server -p $PORT -b 127.0.0.1'
```
and you're all set!
