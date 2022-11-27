---
layout: default
nav_order: 2
parent: API
---

# Multimotor Requests
{: .no_toc}

- TOC
{:toc}

---
GET
{: .fs-5 .v-align-middle .label .label-blue .mx-auto .d-inline}

## /multimotor
{: .d-inline .v-align-middle}

Returns formatting expected for multimotor call.
{: .pt-5 }


### Example
{: .no_toc}
```
localhost:50000/multimotor
```

### Response
{: .no_toc}
```json
```

---

GET
{: .fs-5 .v-align-middle .label .label-blue .mx-auto .d-inline}

## /multimotor/json-body
{: .d-inline .v-align-middle}

Sets multiple motor positions in one API call.
{: .py-5 }

| Argument  | Description                  |
|-----------|------------------------------|
| json-body | json list of motor positions |

### Example
{: .no_toc}
<div class="code-example" markdown="1">
Set motors 23, 24 to 100
</div>
```
localhost:50000/multimotor/...
```

### Response
{: .no_toc}
```json
```

