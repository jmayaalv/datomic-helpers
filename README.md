When populating a Datomic database I found it tedious
 to manually deal with temp IDs to refer entities
 to each other. It is difficult to both write and read.

I created a simple function TO-TRANSATION which accepts
natural Clojure datastructure (nested maps, vectors)
and generates a Datomic transaction to populate DB with
these interlinked entities - temp IDs are assigned automatically,
and references to nested entities (maps) are replaced by their temp IDs.

Also, when working with DB schema, it was inconvenient
to work with plain long list of attributes. I quickly loose
track of how entities are interlinked, difficult to see how I can
improve the schema, difficult to consult it when I write queries.

So TO-SCHEMA-TRANSACTION function helps to generate a schema-defining
transaction from a template, which resembles real shape of data
how we see it through the Entitiy API.

The notation is meat to be intuitively understandable, see [`examples`](datomic_helpers_sample.clj).

The precise rules are specified in the [`source code comments`](src/datomic_helpers.clj).

I think the notation may be improved, but the current
form is enough for me, and helps me significantly.
