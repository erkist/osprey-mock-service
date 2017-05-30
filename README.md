# Osprey Mock Service

Fork of [mulesoft-labs/osprey-mock-service](https://github.com/mulesoft-labs/osprey-mock-service)
that adds the following features:

## Improved examples handling

When several named examples are given for a resource body, using `examples`, there are now two options for how to select which example to return.

1. Select the first example (default behavior)
2. Select example by matching to a provided string (using the `-e` argument)

Given the following example:

```yaml
/resource:
  get:
    responses:
      200:
        application/json:
          examples:
            first-named-example: {"key": "value"}
            second-named-example: {"key": "value2"}
```

By default, this fork of the mock server will return `{"key": "value"}`

To get the mock server to choose a different example, the `-e <substring>` flag can be used. 
The first example where the name contains the `<substring>` will be selected. If no name matches, the first example will be selected.

In the example above, passing `-e sec` will match `second-named-example`, meaning the mock server will return `{"key": "value2"}`

## License

Apache License 2.0