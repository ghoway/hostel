# Reports System

---

# Purpose

Provides operational and financial reporting.

---

# Supported Reports

- Booking reports
- Occupancy reports
- Revenue reports
- Hotel performance reports

---

# Filters

Reports may be filtered by:

- hotel
- date
- booking status

---

# Access Control

Reports access should be permission-based.

# Performance Notes

Large reports and exports SHOULD be processed asynchronously using queues.

Heavy aggregation queries should avoid blocking normal HTTP requests.
