_12/26/2016_

Rspec `assigns` offers easy access to the state of an instance variable at a point in the test without reloading the variable model value.

This code
```ruby
it "changes the contact's attributes" do
  patch :update, id: @contact,
    contact: FactoryGirl.attributes_for(:contact,
      firstname: 'Larry',
      lastname: 'Smith'
    )
  @contact.reload
  expect(@contact.firstname).to eq 'Larry'
  expect(@contact.lastname).to eq 'Smith'
end
```

gives similar result to

```ruby
it "changes the contact's attributes" do
  patch :update, id: @contact,
    contact: FactoryGirl.attributes_for(:contact,
      firstname: 'Larry',
      lastname: 'Smith'
    )
  expect(assigns(:contact).firstname).to eq 'Larry'
  expect(assigns(:contact).lastname).to eq 'Smith'
end
```
