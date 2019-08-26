# Test Cases for Yaml Schema Validation

Test cases for [vscode-yaml](https://github.com/redhat-developer/vscode-yaml) and [yaml-language-server](https://github.com/redhat-developer/yaml-language-server) comparing validation and syntax highlighting output between JSON and YAML files

## Current Test

Conditionally Required with  `if...then`

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

| Lang | Expected               | Passed |
| ---- | ---------------------- | ------ |
| Yaml | Require prop "options" | ✔      |
| Json | Require prop "options" | ✔      |

## Links

* Spec
  * [6.6 Keywords for Applying Subschemas Conditionally](http://json-schema.org/latest/json-schema-validation.html#rfc.section.6.6)
  * [6.7 Keywords for Applying Subschemas With Boolean Logic](http://json-schema.org/latest/json-schema-validation.html#logic)

* Guides
  * [Applying subschemas conditionally](https://json-schema.org/understanding-json-schema/reference/conditionals.html)
  * [Combining schemas](https://json-schema.org/understanding-json-schema/reference/combining.html)

* Stack Overflow
  * [JsonSchema - conditionally require attribute](https://stackoverflow.com/a/38781027/1366033)
