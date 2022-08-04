# textual-object
A solution for embedding and reading object data from plain texts stored in local storage.

# Why textual-object solution

We want:
1. to not to lose data when the source, e.g. a piece of software, is down.
2. to not to lose all of the data when even the local storage is gone, and only the text is left.
3. 

# Components

## Textual object store: TOF

A local store for TO object saved in JSON format.

---


## Textual object markup language: TOL

The language used for markers embedded in the text which is readable and contains metadata point to its entry in the local store.

---

# TOL Marker format

TOL marker is a short and succint textual representation of an entry in TOF.

## TOL Marker Format

The TOL market format is simple and fully readable:

- Default: `[[KEY 1: Value 1|KEY 2: VALUE 2| KEY x: VALUE x ...]]`

You could type it by hand, but it's highly recommended to let [TOE](#TOE) generate the marker for you, at least the key information, such as the ID and SID.

You can also customize the symbol to your liking or to avoid conflicts with some other Plain languages. For example:

- Customized: `{{KEY 1: Value 1| Key 2: Value 2| Key 3: Value 3...}}`

# TOL Fields

The following fields are required and optional, but the key words are reserved. You can add any key-value pairs as you want, but you cannot use the follow keywords.
E.g. 
```
Acceptable: {{ID: 123|SERIAL_NUMBER: XXX}}
Unacceptable: {{ID: 123| ID: 456}}
- In this case the second value is ignored.

```
### Required fields:

- ID: a locally (in the store file) unique identifier for the entry. Used to look up for the entry in the local TO store (TOF)

### Optional fields:
- Source: the name of the source of the TO entry. Such as Zotero, webpage, Elastic database etc.
- SID: the source specific unique identifier. Used to look up for the entry in the source, for example, in a database or on the web.
- 

Example:

[[ID: xxx; ]]

# TOE: Textual object engine
