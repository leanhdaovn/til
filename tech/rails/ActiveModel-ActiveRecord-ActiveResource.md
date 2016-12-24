_12/24/2016_

# ActiveRecord vs ActiveModel vs ActiveResource

##### TL;DR
- ActiveModel = functionality to operate model object
- ActiveRecord = ActiveModel + persist to Database
- ActiveResource = ActiveModel + call external Web Services

---

#### ActiveRecord
- Associates a class to the database. It is an implementation of the Active Record pattern for an ORM (Data Mapper pattern is an alternative).
- Provides functionality to operate model object, persist and retrieve data to and from database.

---

#### ActiveModel
- Extracted from ActiveRecord since rails 3.
- Provides functionality to operate model without persisting to database.

---

#### ActiveResource
- Connects business objects and Representational State Transfer (REST) web services.
- Provide functionality to operate model object.
