# Domain Model

Coworking space reservation system (GambaDesk).

## Entities
| Entity | Meaning | Notes |
|---|---|---|
| User | Person using the system (Customer or Administrator) | Breeze auth, `users` table |
| Space | Physical coworking area (e.g. "Sala A", "Planta 1") | Future entity |
| Desk | Individual bookable desk within a space | Future entity |
| Reservation | Booking of a desk by a customer for a time period | Future entity |

## Relationships
- User (Customer) has many Reservations
- Space has many Desks
- Desk has many Reservations
- User (Administrator) manages Spaces and Desks

## Business Rules
- Only authenticated customers can create reservations
- Administrators can manage spaces, desks, and reservation states
- A desk cannot be double-booked for overlapping time slots
- Reservation states: pending, confirmed, cancelled, completed
- Administrators can cancel or confirm any reservation
- Customers can cancel their own reservations (before a configurable cutoff)
- Registration requires email verification

## Glossary
| Term | Meaning |
|---|---|
| Customer | End user who registers, logs in, and books desks |
| Administrator | User who manages spaces, desks, and all reservations |
| Space | Physical coworking area containing desks |
| Desk | Individual bookable unit within a space |
| Reservation | Booking record linking a customer to a desk for a time range |
| Coworking | Shared workspace environment where members book desks flexibly |
