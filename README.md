# Unstructured changes

Adds an unstructuredChanges array to the Amendment object.

## Legal context

See [OCDS for the European Union](http://standard.open-contracting.org/profiles/eu/master/en/F14) for guidance on how to use it with TED F14 data.

## Example

```json
{
  "tender": {
    "amendments": [
      {
        "id": "1",
        "unstructuredChanges": [
          {
            "oldValue": {
              "text": "https://city.example.org/procurement"
            },
            "newValue": {
              "text": "https://procurement.example.org"
            },
            "where": {
              "section": "I.1",
              "label": "Main address"
            }
          },
          {
            "oldValue": {
              "classifications": [
                {
                  "scheme": "CPV",
                  "id": "79000000"
                }
              ]
            },
            "newValue": {
              "classifications": [
                {
                  "scheme": "CPV",
                  "id": "79822500"
                }
              ]
            },
            "where": {
              "section": "II.2.2",
              "label": "Main CPV code"
            },
            "relatedLot": "lot-2"
          }
        ]
      }
    ]
  }
}
```

## Issues

Report issues for this extension in the [ocds-extensions repository](https://github.com/open-contracting/ocds-extensions/issues), putting the extension's name in the issue's title.

## Changelog

### 2020-06-04

* Review normative and non-normative words.

### 2020-04-24

* Add `minProperties`, `minItems` and/or `minLength` properties.

This extension was originally discussed as part of the [OCDS for EU profile](https://github.com/open-contracting-extensions/european-union/issues/63) and in [pull requests](https://github.com/open-contracting-extensions/ocds_unstructuredChanges_extension/pulls?q=is%3Apr+is%3Aclosed).
