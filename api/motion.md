---
layout: default
nav_order: 3
parent: API
---

# Motion Requests
{: .no_toc}

- TOC
{:toc}

---
GET
{: .fs-5 .v-align-middle .label .label-blue .mx-auto .d-inline}

## /motion
{: .d-inline .v-align-middle}

List all motions.
{: .pt-5 }


### Example
{: .no_toc}
```
localhost:50000/motion
```

### Response
{: .no_toc}
```json
{
  "data": [
    {
      "id": 0,
      "name": "basic_motion",
      "button": "A"
    },
	...
    {
      "id": 13,
      "name": "pc_control",
      "button": "A"
    }
  ],
  "message": "findAllMotions"
}
```

---

GET
{: .fs-5 .v-align-middle .label .label-blue .mx-auto .d-inline}

## /motion/id
{: .d-inline .v-align-middle}

Returns information on motion `id`
{: .py-5 }

| Argument | Description            | Range |
|----------|------------------------|-------|
| id       | Motion id              | 0-13  |

### Example
{: .no_toc}
<div class="code-example" markdown="1">
Return information on motion 1
</div>
```
localhost:50000/motion/1
```

### Response
{: .no_toc}
```json
{
  "data": {
      "id": 1,
      "name": "kick_right",
      "button": "B"
    },
      "message": "getMotionInfo"
}
```

---

GET
{: .fs-5 .v-align-middle .label .label-blue .mx-auto .d-inline}

## /motion/name
{: .d-inline .v-align-middle}

Executes motion `name` and returns motion information.
{: .py-5 }

| Argument | Description    |
|----------|----------------|
| name     | Motion name    |

### Example
{: .no_toc}
<div class="code-example" markdown="1">
Execute `basic_motion`
</div>
```
localhost:50000/motion/basic_motion
```

### Response
{: .no_toc}
```json
{
  "data": {
      "id": 0,
      "name": "basic_motion",
      "button": "A"
    },
      "message": "execMotion"
}
```
