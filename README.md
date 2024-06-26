# igdb_client
Ruby client interface for IGDB API. Supports API v4.

## Installation
```ruby
$ gem install igdb_client
```

## Usage
The structure of queries and results matches the [api documentaion.](https://api-docs.igdb.com/)
You will need client id and a client secret to access the API. The above link explains how to
acquire them.

Please note, that unlike the previous versions, this client takes a client secret rather
than access token. The client will retrieve the required access token and renew it
whenever it expires.

##### Instance
```ruby
require 'igdb_client'

# initialize with client id and token
client = IGDB::Client.new("client_id","client_secret")

# pass endpoint and fields
client.get "games", {fields: "name", limit: 10}

# Use search method to search
client.search("ibb and obb", {fields: "name,release_dates,rating"})

# Use id if you want to match by id
client.id 1942

# Access retrieved data by using methods matching fields of data
results = client.platform.id 2
results[0].name
results[0].summary
```
