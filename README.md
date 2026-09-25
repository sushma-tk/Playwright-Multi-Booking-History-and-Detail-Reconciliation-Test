# Playwright - EventHub Multi Booking History and Detail Reconciliation

An end-to-end Playwright test for the [EventHub](https://eventhub.rahulshettyacademy.com) practice app.
It creates two bookings in one session and checks that both appear correctly in **My Bookings** and on their detail pages, matched by **booking reference**, never by list position.

## What the test does

1. Logs in once for the whole session.
2. Books **World Tech Summit** (Conference, Hyderabad, search "World", 1 ticket).
3. Books **Dilli Diwali Mela** (Festival, Delhi, search "Dilli", 2 tickets).
4. Captures each booking's reference, title, tickets, total, and customer email from the confirmation page.
5. Opens My Bookings and finds each card by its booking reference.
6. Checks each card shows confirmed status, title, ticket count, and total.
7. Opens each booking's detail page and checks:
   - Breadcrumb reference
   - Event title
   - Customer email
   - Payment summary (tickets and total)
   - Numeric booking ID
   - That the other booking's reference and title do not appear (no mix-up)

## Tech used

- Playwright (JavaScript)
- Chromium

## How to run

```
npx playwright test
```

## Notes

- A reusable `createBooking()` function handles search, filters, booking, and returns the booking details.
- Cards are found with `filter({ hasText: bookingRef })`, so old bookings from previous runs don't affect the test.

