notes
=====

### Summary

My web development notes, snippets, and whatnot.

Development
=====

Ruby
-----

### Hash

###### [Dig](http://ruby-doc.org/core-2.3.0/Hash.html#method-i-dig)

Ruby 2.3.0 added a cool new method for Hashes. `Hash.dig` lets me dive in the Hash without that ugly bracket notation.

Here's a sample Hash of some weather conditions.

```ruby
conditions = {:currently=>{:summary=>"Partly Cloudy", :temperature=>72.3, :apparentTemperature=>72.3, :dewPoint=>70.34, :humidity=>0.94, :windSpeed=>3.95, :windBearing=>21, :visibility=>7.22, :cloudCover=>0.3, :pressure=>1023.42, :ozone=>249.06}}
```

Previously, I've done something like `conditions[:currently][:summary]` to return `"Partly Cloudy"`.

But with `Hash.dig`, I can do `conditions.dig :currently, :summary`. It achieves the same result, but the key is in the errors.

If there's an error in the first example, it fails with `NoMethodError`. If there's an error in the `Hash.dig` method, it will just return nil.

Ruby on Rails
-----

### [Searchkick](http://searchkick.org)


###### Partial Match

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
