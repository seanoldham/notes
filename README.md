notes
=====

### Summary

My web development notes, snippets, and whatnot.

Development
=====

Rails
-----

### Searchkick

###### Partial Match

Can do [partial matches](https://github.com/ankane/searchkick#partial-matches). I followed the README and added this to my Drawing model:
```ruby
searchkick  text_end: [:number], text_middle: [:number]
```

However, when I went to make it run, after `reindex` of course, instead of doing
```ruby
Drawing.search(params[:term], limit: 30, fields: [:number], match: [:text_end, :text_middle])
```
I had to squish them together like
```ruby
Drawing.search(params[:term], limit: 30, fields: [{number: :text_end, number: :text_middle}])
```
