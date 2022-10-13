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
## Stand Up
{: .d-inline}

POST
{: .label .label-blue .mx-auto .d-inline}

### Example
{: .no_toc}
```
localhost:3000/move/stand-up
```

### Response
{: .no_toc}
```json
{
    "response":"1"
}
```

### Notes
{: .no_toc}
If response is not 1, see maintenance manual for error codes.

---
## Motor Information
{: .d-inline}

GET
{: .label .label-green .mx-auto .d-inline}

### Example
{: .no_toc}
```
localhost:3000/motor/31
```

### Response
{: .no_toc}
```json
{
    "angle":"270",
    "status":"1"
}
```

### Notes
{: .no_toc}
Status 1 means motor is currently locked by the serial port.

