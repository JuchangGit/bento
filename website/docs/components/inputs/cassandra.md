---
title: cassandra
type: input
status: experimental
categories: ["Services"]
---

<!--
     THIS FILE IS AUTOGENERATED!

     To make changes please edit the contents of:
     lib/input/cassandra.go
-->

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

:::caution EXPERIMENTAL
This component is experimental and therefore subject to change or removal outside of major version releases.
:::
Executes a find query and creates a message for each row received.


<Tabs defaultValue="common" values={[
  { label: 'Common', value: 'common', },
  { label: 'Advanced', value: 'advanced', },
]}>

<TabItem value="common">

```yml
# Common config fields, showing default values
input:
  label: ""
  cassandra:
    addresses: []
    query: ""
    timeout: 600ms
```

</TabItem>
<TabItem value="advanced">

```yml
# All config fields, showing default values
input:
  label: ""
  cassandra:
    addresses: []
    password_authenticator:
      enabled: false
      username: ""
      password: ""
    disable_initial_host_lookup: false
    query: ""
    max_retries: 0
    backoff:
      initial_interval: ""
      max_interval: ""
    timeout: 600ms
```

</TabItem>
</Tabs>

## Examples

<Tabs defaultValue="Minimal Select (Cassandra/Scylla)" values={[
{ label: 'Minimal Select (Cassandra/Scylla)', value: 'Minimal Select (Cassandra/Scylla)', },
]}>

<TabItem value="Minimal Select (Cassandra/Scylla)">


Let's presume that we have 3 Cassandra nodes, like in this tutorial by Sebastian Sigl from freeCodeCamp:

https://www.freecodecamp.org/news/the-apache-cassandra-beginner-tutorial/

Then if we want to select everything from the table users_by_country, we should use the configuration below.
If we specify the stdin output, the result will look like:

{"age":23,"country":"UK","first_name":"Bob","last_name":"Sandler","user_email":"bob@email.com"}

This configuration also works for Scylla.


```yaml
input:
  cassandra:
    addresses:
      - 172.17.0.2
    query:
      'SELECT * FROM learn_cassandra.users_by_country'
```

</TabItem>
</Tabs>

## Fields

### `addresses`

A list of Cassandra nodes to connect to.


Type: `array`  

### `password_authenticator`

Optional configuration of Cassandra authentication parameters.


Type: `object`  

### `password_authenticator.enabled`

Whether to use password authentication


Type: `bool`  

### `password_authenticator.username`

A username


Type: `string`  

### `password_authenticator.password`

A password


Type: `string`  

### `disable_initial_host_lookup`

If enabled the driver will not attempt to get host info from the system.peers table. This can speed up queries but will mean that data_centre, rack and token information will not be available.


Type: `bool`  

### `query`

A query to execute.


Type: `string`  

### `max_retries`

The maximum number of retries before giving up on a request.


Type: `int`  

### `backoff`

Control time intervals between retry attempts.


Type: `object`  

### `backoff.initial_interval`

The initial period to wait between retry attempts.


Type: `string`  

### `backoff.max_interval`

The maximum period to wait between retry attempts.


Type: `string`  

### `timeout`

Sorry! This field is missing documentation.


Type: `string`  
Default: `"600ms"`  

```yml
# Examples

timeout: 600ms
```

