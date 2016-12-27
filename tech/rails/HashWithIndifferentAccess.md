_12/27/2016_

# HashWithIndifferentAccess

```Ruby
ActiveSupport::HashWithIndifferentAccess
```

is a hash that offers access via both symbol and string keys

Normal hash
```ruby
h = {foo: 1, 'bar' => 2}

h[:foo] #=> 1
h['bar'] #=> 2

h['foo'] #=> nil
h[:bar] #=> nil
```

HashWithIndifferentAccess

```ruby
h = HashWithIndifferentAccess.new(foo: 1, 'bar' => 2)

h[:foo] #=> 1
h['bar'] #=> 2

h['foo'] #=> 1
h[:bar] #=> 2
```
