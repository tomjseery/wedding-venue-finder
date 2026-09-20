# Wedding Venue Finder

A responsive PHP and MySQL coursework application for finding wedding venues that match a date, party size and catering grade. The browser submits the search asynchronously and presents matching venues with capacity, licensing, catering costs, base prices and calculated totals.

## Features

- Single-page home and venue-search experience
- Responsive Bootstrap layout and image carousel
- AJAX search without a full page reload
- Capacity and catering-grade filtering
- Exclusion of venues already booked on the selected date
- Weekday/weekend pricing with per-person catering costs
- JSON response rendered as a results table

## Technology

- PHP and MySQL/MariaDB
- HTML, CSS and JavaScript
- jQuery AJAX
- Bootstrap

## Local setup

The original database and credentials file are not included. Create a MySQL or MariaDB database containing the tables and columns referenced by the query:

| Table | Referenced columns |
| --- | --- |
| `venue` | `venue_id`, `name`, `capacity`, `licensed`, `weekday_price`, `weekend_price` |
| `venue_booking` | `venue_id`, `booking_date` |
| `catering` | `venue_id`, `grade`, `cost` |

Create `coa123-mysql-connect.php` beside `weddingprocess.php` and define `$servername`, `$username`, `$password` and `$dbName`. Keep that file out of version control.

For a simple development server:

```sh
php -S localhost:8000
```

Then open `http://localhost:8000/wedding.php`.

## Request flow

1. `wedding.php` collects the date, party size and catering grade.
2. jQuery sends the values to `weddingprocess.php`.
3. PHP queries venue, booking and catering data.
4. Matching rows are returned as JSON and rendered in the browser.

## Status and security

This repository preserves a historical university exercise. It demonstrates joins, aggregate queries, subqueries and AJAX integration, but it is not production-ready. The current SQL interpolates request values directly; a real deployment must use server-side validation and prepared statements before accepting untrusted input.
