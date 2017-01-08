_08/01/2017_

## Safe Navigation Operator: Ampersand Dot (&.)

Introduced in Ruby 2.3, this operator helps us call methods on an object without worrying if it's `nil` or not.

With old syntax, we have to check for `nil` cases

```ruby
if @person && @person.spouse && @person.spouse.name
  name = @person.spouse.name.upcase
end
# or
name = @person.try(:spouse).try(:name).try(:upcase)
```

With Safe Navigation Operator

```ruby
name = @person&.spouse&.name&.upcase
```
