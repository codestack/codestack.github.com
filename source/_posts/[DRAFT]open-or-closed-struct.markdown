While reading the great Avdi's [Objects on Rails](http://objectsonrails.com/) I've came accross some interesting
code I didn't understand really well.

Take a look at this
```ruby
# spec/models/blog_spec.rb
require 'ostruct'
describe Blog do
  # ...
  describe "#new_post" do
    before do
      @new_post = OpenStruct.new
      @it.post_source = ->{ @new_post }
    end
    it "returns a new post" do
      @it.new_post.must_equal @new_post
    end
    it "sets the post's blog reference to itself" do
      @it.new_post.blog.must_equal(@it)
    end
  end
end
```
Avdi simply explains this spec with

{% blockquote %}
Here, we substitute a lambda which simply returns an OpenStruct for the
#post_source. 
{% endblockquote %}
