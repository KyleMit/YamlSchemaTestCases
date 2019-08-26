# Test Cases for Yaml Schema Validation

Test cases for [vscode-yaml](https://github.com/redhat-developer/vscode-yaml) and [yaml-language-server](https://github.com/redhat-developer/yaml-language-server) comparing validation and syntax highlighting output between JSON and YAML files

## Resources & Refernces

* Spec
  * [6.6 Keywords for Applying Subschemas Conditionally](http://json-schema.org/latest/json-schema-validation.html#rfc.section.6.6)
  * [6.7 Keywords for Applying Subschemas With Boolean Logic](http://json-schema.org/latest/json-schema-validation.html#logic)

* Guides
  * [Applying subschemas conditionally](https://json-schema.org/understanding-json-schema/reference/conditionals.html)
  * [Combining schemas](https://json-schema.org/understanding-json-schema/reference/combining.html)
  * [Schema Dependencies](https://json-schema.org/understanding-json-schema/reference/object.html#schema-dependencies)

* Stack Overflow
  * [JsonSchema - conditionally require attribute](https://stackoverflow.com/a/38781027/1366033)

## Tests

### Conditionally Require Field

### Conditionally Require Field ... Results

| Lang | Expected               | Passed |
| ---- | ---------------------- | ------ |
| Yaml | Require prop "options" | ✅     |
| Json | Require prop "options" | ✅     |

![screenshot](https://i.imgur.com/p8sNT7n.png)

### Conditionally Require Field .... with  `if...then`

```json
"if": {
  "properties": {
    "controlType": {"const": "dropdown"}
  }
},
"then": {
  "required": ["options"]
}
```

### Conditionally Require Field .... with `anyOf` or `oneOf`

```json
"oneOf": [
  {
    "properties": {
      "controlType": {"const": "dropdown"}
    },
    "required": ["options"]
  },
  {
    "properties": {
      "controlType": {"const": "button"}
    }
  }
]
```

## Conditionally Add Property

### Conditionally Add Property ... Results

![screenshot](https://i.imgur.com/HmWFCjY.png)

| Lang | Expected                   | Passed |
| ---- | -------------------------- | ------ |
| Yaml | Autocomplete for "options" | ❌     |
| Json | Autocomplete for "options" | ✅     |

### Conditionally Add Property ... with  `if...then`

```json
"if": {
  "properties": {
    "controlType": {"const": "dropdown"}
  }
},
"then": {
  "properties": {
    "options": {
      "type": "array",
      "items": {"type": "string"}
    }
  }
}
```
