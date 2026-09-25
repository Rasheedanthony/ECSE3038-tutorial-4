# Tutorial 4 — Idempotence notes

| # | Request | Status | Devices after |
| --- | --- | --- | --- |
| 9 | POST /devices with the probe body | 201 | 5 |
| 10 | POST /devices with the probe body again | 201 | 6 |
| 11 | GET /devices/probe | 200 | 6 (only one probe returned) |
| 12 | PUT /devices/attic with the attic body | 200 | 6 |
| 13 | PUT /devices/attic with the attic body again | 200 | 6 |
| 14 | DELETE /devices/fridge | 200 | 5 |
| 15 | DELETE /devices/fridge again | 404 | 5 |

## Answer

PUT and DELETE are idempotent. Sending the same PUT twice left the attic device the same and the count stayed at 6. Sending DELETE twice gave a 404 the second time, but the count stayed at 5, so the state didn't change. POST is not idempotent because sending it twice added two probe devices and the count went from 5 to 6.