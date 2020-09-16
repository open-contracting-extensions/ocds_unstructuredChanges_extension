# Unstructured changes

Adds an unstructuredChanges array to the Amendment object.

# Guidance

In many procurement regimes, it is common to amend a procurement notice by describing the changes in words, rather than by re-publishing the full notice. This is because the process is designed for humans: it is easier for a human to read a description of changes, than to calculate the difference between two full notices.

On the other hand, it is easy for a machine to calculate the difference between two full notices, but difficult or impossible to interpret a description of changes. There are many ways in which a change description can go wrong, which a human can recover from, but which a machine cannot. For example:

- the label of the field that is subject to modification can refer to
  - non-existent sections or labels
  - existent but incorrect labels
- the type of the new value can be inconsistent with the type of the field

OCDS is designed to be read by machines. Ideally, the source system from which OCDS data is exported contains the values of each field before and after a change. In that case, you should simply follow [the releases and records model](https://standard.open-contracting.org/latest/en/schema/reference/#release-handling).

This extension is intended to be used only in cases where a source system doesn't track the values of fields, but instead tracks a description of changes, like in the EU (see Legal context). However, the lack of structure will not allow you to do so much data analysis.

## Legal context

We developed this extension primarily to enable the mapping TED form F14 XML to OCDS, but it can also be useful in non-EU contexts.

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
              "date": "2020-12-15"
            },
            "newValue": {
              "date": "2019-12-15T14:00:00+03:00"
            },
            "where": {
              "section": "I.4",
              "label": "Notice date"
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

### 2020-09-16

* Add guidance highlighting the difference between structured and unstructured changes

### 2020-07-13

* Relax date format to allow either date or datetime

### 2020-06-04

* Review normative and non-normative words.

### 2020-04-24

* Add `minProperties`, `minItems` and/or `minLength` properties.

This extension was originally discussed as part of the [OCDS for EU profile](https://github.com/open-contracting-extensions/european-union/issues/63) and in [pull requests](https://github.com/open-contracting-extensions/ocds_unstructuredChanges_extension/pulls?q=is%3Apr+is%3Aclosed).
