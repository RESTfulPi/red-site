---
layout: default
nav_order: 1
parent: API
---

# Requests
{: .no_toc}

This page lists all of the available requests in the API.

- TOC
{:toc}

---
## Manual motor control
{: .d-inline}

POST
{: .label .label-blue .mx-auto .d-inline}

Used to manually set the position of a motor.

| Argument | Description        | Range |
|:---------|:-------------------|:------|
| id       | The motor ID       | 1-25  |
| position | The motor position | 0-254 |


### Example
{: .no_toc}
```
localhost:50000/motor/23/127
```

### Response
{: .no_toc}
```json
```

### Notes
{: .no_toc}

---

## Play motion
{: .d-inline}

POST
{: .label .label-blue .mx-auto .d-inline}

Used to execute a predefined motion on the robot.

| Argument | Description            |
|:---------|:-----------------------|
| name     | The name of the motion |

### Example
{: .no_toc}
```
localhost:50000/motion/gangnam-style
```

### Response
{: .no_toc}
```json
```

### Notes
{: .no_toc}

