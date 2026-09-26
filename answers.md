# Tutorial 4 — Idempotence notes



PUT and DELETE are idempotent. Sending the same PUT twice left the attic device the same and the count stayed at 6. Sending DELETE twice gave a 404 the second time, but the count stayed at 5, so the state didn't change. POST is not idempotent because sending it twice added two probe devices and the count went from 5 to 6.
