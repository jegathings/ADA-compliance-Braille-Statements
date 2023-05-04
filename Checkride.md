# ADA Compliance-Braille System
Define an event streaming system that ultimately prints messages.

From the **Problem Statement**, aka README.md.
```
PCOE provides printing services that print statements, notices, and marketing materials. They have the capability to print regular non-Braille letters in house (with full control of the printing software) and now Braille which is done by an external vendor (through a REST interface), required by ADA.
```

Problem solution:
```
This solution will model the printing services as events.  The following events have been identified based on the above statement:
```
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

```
The previously defined events will be handled by individual producers.
```
### Defined Producers
+ Statement Producer
+ Notice Producer
+ Marketing Producer
+ Non Braile Producer
+ Braile Producer

```
The previously defined events will perform SQL operations to create a payload.  SQL can be used to gather stateful information such as the type of statement (Marketing, Braile, Non Braile, etc).  SQL can also have templated statements (Marketing, Braile, Non Braile) and the producer can create a dynamic message based off the SQL results.
```
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
+ Statement Template
  + The templates are parameratized and the paramerters can be substited by the producer.
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

