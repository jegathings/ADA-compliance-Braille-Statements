# ADA Compliance-Braille System
Define an event streaming system that ultimately prints messages.

### Print Stream Events
+ Statement
+ Notice
+ Marketing materials
+ Non Braile
  + In-house service
  + We have full control of the service
+ Braile
  + External vendor via RESTful services
  + This is required by ADA

### Defined Producers
+ Statement Producer
+ Notice Producer
+ Marketing Producer
+ Non Braile Producer
+ Braile Producer

### Producer Tables
+ Statement Table
  + Joins with Customer
+ Notice Table
  + Joins with Customer
+ Marketing Table
  + Joins with Customer
+ Non Braile Table
  + Joins with Customer
+ Braile Table
  + Joins with Customer

### Statement Producer
```
Statement Producer will use a SQL inner join statement between the customer and statement tables.  Next, the producer will take the SQL results and produce events to the broker.  The event key will be "statement".  The event value will be the statement payload.
```

### Notice Producer
```
Notice Producer will use a SQL inner join statement between the customer and notice tables.  Next, the producer will take the SQL results and produce events to the broker.  The event key will be "notice".  The event value will be the notice payload.
```

### Marketing Producer
```
Marketing Producer will use a SQL inner join statement between the customer and statement tables.  Next the marketing producer will take the SQL results and produce events to the broker.  The event key will be "marketing".  The event value will be the marketing payload.
```

### Non Braile Producer
```
Non Braile Producer will use a SQL inner join statement between customer and non-braile tables.  Next the braile producer will take the SQL results and produce events to the broker.  The event key will be "non-braile".  The event value will be the non-braile payload.
```

### Braile Producer
```
The Braile Producer will use a SQL inner join statment between customer and braile tables.
Next, the Braile Producer will need to use a RESTful webservice to contact the external vendor to generate the payload.  The producer will publish the braile events to the broke.  The event key will be "braile".  The event value will the braile payload.
```

### Marketing Producer
```
Marketing Producer will use a SQL inner join statement between the customer and marketing tables.  Next, the producer will take the SQL results and produce events to the broker.  The event key will be "marketing".  The event value will be the marketing payload.
```

### Defined Consumers
+ Statement Consumer
+ Notice Consumer
+ Marketing Consumer
+ Non Braile Consumer
+ Braile Consumer

### Consumer Tables
+ processed_records
  + customer_id, print_status, print_timestamp, consumer_type
+ consumer_type
  + Statement
  + Notice
  + Marketing
  + Non Braile
  + Braile

