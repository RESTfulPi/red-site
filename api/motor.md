---
layout: default
nav_order: 1
parent: API
---

# Motor Requests
{: .no_toc}

- TOC
{:toc}

---
GET
{: .fs-5 .v-align-middle .label .label-blue .mx-auto .d-inline}

## /motor
{: .d-inline .v-align-middle}

List all motor information.
{: .pt-5 }


### Example
{: .no_toc}
```
localhost:50000/motor
```

### Response
{: .no_toc}
```json
{
  "data": [
    {
      "id": 0,
      "name": "left-foot",
      "description": "foot tilt in/out",
      "position": 0,
      "min": 115,
      "max": 140,
      "default": 127,
      "inverted": true
    },
	...
    {
      "id": 24,
      "name": "head",
      "description": "look up/down",
      "position": 0,
      "min": 70,
      "max": 160,
      "default": 127,
      "inverted": false
    }
  ],
  "message": "getAllMotors"
}
```

---

GET
{: .fs-5 .v-align-middle .label .label-blue .mx-auto .d-inline}

## /motor?id=
{: .d-inline .v-align-middle}

Returns status of motor.
{: .py-5 }

| Argument | Description            | Range |
|----------|------------------------|-------|
| id       | Motor id               | 0-24  |

### Example
{: .no_toc}
<div class="code-example" markdown="1">
Return the status of motor 23
</div>
```
localhost:50000/motor?id=23
```

### Response
{: .no_toc}
```json
{
  "data": {
    "id": 23,
    "name": "neck",
    "description": "look left/right",
    "position": 0,
    "min": 1,
    "max": 254,
    "default": 127,
    "inverted": false
  },
  "message": "getMotorInfo"
}
```

---

GET
{: .fs-5 .v-align-middle .label .label-blue .mx-auto .d-inline}

## /motor?id=&position=
{: .d-inline .v-align-middle}

Moves motor to `position` and returns motor status.
{: .py-5 }

| Argument | Description    | Range |
|----------|----------------|-------|
| id       | Motor id       | 0-24  |
| position | Motor position | 0-100 |

### Example
{: .no_toc}
<div class="code-example" markdown="1">
Set motor 23 to position 100 and return status
</div>
```
localhost:50000/motor?id=23&position=100
```

### Response
{: .no_toc}
```json
{
  "data": {
    "id": 23,
    "name": "neck",
    "description": "look left/right",
    "position": 0,
    "min": 1,
    "max": 254,
    "default": 127,
    "inverted": false
  },
  "message": "setMotorPos",
  "smartPosition": "1",
  "rawPosition": 4
}
```

---

GET
{: .fs-5 .v-align-middle .label .label-blue .mx-auto .d-inline}

## /motor?id=&position=&torq=
{: .d-inline .v-align-middle}

Moves motor to `position` with torque of `torq` and returns motor status.
{: .py-5 }

| Argument | Description    | Range |
|----------|----------------|-------|
| id       | Motor id       | 0-24  |
| position | Motor position | 0-100 |
| torq     | Motor torque   | 0-4   |

### Example
{: .no_toc}
<div class="code-example" markdown="1">
Set motor 23 to position 100 with a torque of 4 and return status
</div>
```
localhost:50000/motor?id=23&position=100&torq=4
```

### Response
{: .no_toc}
```json
{
  "data": {
    "id": 23,
    "name": "neck",
    "description": "look left/right",
    "position": 0,
    "min": 1,
    "max": 254,
    "default": 127,
    "inverted": false
  },
  "message": "setMotorPos",
  "smartPosition": "1",
  "rawPosition": 4
}
```
