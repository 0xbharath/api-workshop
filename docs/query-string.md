API Workshop - Url Structure

## Sections:

* [Bread Crumb Navigation](#bread-crumb-navigation)

#### Query Component of URL

[RFC 3986 Section 3.4](https://tools.ietf.org/html/rfc3986#section-3.4)

The query component contains non-hierarchical data that, along with data in the path component, serves to identify a resource within the scope of the URI's scheme and naming authority (if any).

The query component is indicated by the first question mark ("?") character and terminated by a number sign ("#") character or by the end of the URI.


The characters slash ("/") and question mark ("?") may represent data within the query component.

#### Query Component Example

`http://api.walmartlabs.com/v1/search?query=chromebook&format=json&apiKey=AKey12345`

The query string here start after the `?` character

So in this query you have the following pairs that are separated by the `&` delimiter:

1. `query=chromebook`
2. `format=json`
3. `apiKey=AKey12345`

#### HTML Web Forms

[Web Forms](https://en.wikipedia.org/wiki/Query_string#Web_forms)

When a HTML Form is submitted the content of the form is encoded as follows:

`field1=value1&field2=value2&field3=value3...`

The query string is composed of a series of field-value pairs.

Within each pair, the field name and value are separated by an equals sign, '='.

The series of pairs is separated by the ampersand, '&' (or semicolon, ';' for URLs embedded in HTML and not generated by a `<form>...</form>`.

#### Result filtering

When doing a filtering action with a query string parameter than think about using a unique query parameter

For instance to get a particular student from a list:

```http
GET /students?id=5
```

#### Sorting

A simple sorting example can be illustrated here:

```http
GET /users?sort=id
```

Here we sort a list of users by ID

If we wanted to have a more advanced sorting feature we could perhaps do the following:

```http
GET /users?sort=-id,grade
```

Here we have a comma separated list and use the `-` to denote descending sort order and additionally sort by grade

#### Searching

At times you need more powerful constructs so you could use something like Elastic search or any other technology based on [Apache Lucene](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html) that does full text search.

```curl
curl -XGET 'localhost:9200/_search?q=logged'
```

Notice here that we use `q=logged` for our search query with Elastic Search.

#### Limit payload information that resources return

The API consumer doesn't always need the full information returned from a particular resource.
Mobile clients can especially take advantage of this feature if you provide it.

You can use a fields query parameter which takes a comma separated list.

```http
GET /students?fields=id,name,grade
```

This query will only return the fields: `id`, `name`, and `grade`

#### Bread Crumb Navigation
_________________________

Previous | Next
:------- | ---:
← [URI Design](./uri-design.md) | [API Design](./api-design.md) →