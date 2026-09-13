# Features and functionality

What the system does, by the person using it. Every item here is implemented in the
production application; nothing is aspirational.

---

## Roles

One build, five role views. The role decides which tabs exist and what the API
returns — a housekeeper and an owner open the same URL and get different systems.

| Role | What they see |
|---|---|
| **Housekeeping** | Assigned rooms, their own tasks, their own leave and pay |
| **Supervisor** | The floors they oversee, room updates, damage reporting |
| **Front desk** | Live occupancy, check-in and check-out, guest allocation |
| **Manager** | Task assignment, leave approval, staff pay tracking |
| **Admin / owner** | All of the above, plus staff records, payroll and reporting |

---

## Rooms

- **Live status board** across every floor, colour-coded and grouped, showing at a
  glance what is occupied, clean, dirty, being cleaned, under maintenance, damaged,
  or due to check out.
- **Occupancy counters** at the top — occupied, clean, dirty, maintenance,
  checkout — so the shape of the property is readable in one second.
- **Guest name, check-in and check-out dates** held against the room, with a
  "checkout today" marker and a running day count for current stays.
- **Maintenance is an interruption, not a step.** The system remembers what a room
  was before it was flagged, and returns it there once the repair is done, rather
  than leaving someone to guess.
- **Remarks** on any room for anything that does not fit a status.

## Housekeeping

- **Rooms are assigned to a named person**, not to "whoever is on that floor".
- **Daily services** tracked per stay — what was done, on which day, by whom, and
  whether it was completed or deliberately skipped.
- **Guest add-ons** with their own small lifecycle: requested, delivered, pending
  collection, returned, or cancelled. Extra towels that went out get collected
  back, and the system knows which rooms are still holding items.
- **Damage reporting with photographs**, so a fault is recorded with evidence
  rather than described second-hand.
- **Emergency mode** for situations that need every available hand redirected.

## Tasks

- **Assign work to a specific person** with a title, description, priority and due
  date.
- **Three states** — pending, in progress, done — updated by the person doing the
  work.
- **Photo attachments** for tasks that need showing rather than telling.
- **Filter by state**, so a manager can see only what is outstanding.
- **Push notification on assignment**, so work reaches a phone rather than waiting
  to be discovered.

## Duty and attendance

- **Staff go on and off duty in the app**, and every change is timestamped.
- **Live staff status** shows who is currently on shift and when they started.
- This record is what payroll is later derived from, so attendance is captured as
  it happens rather than reconstructed from memory.

## Payroll

- **Derived from recorded attendance** — working days, days present, days absent.
- **Deductions calculated from absence**, with **bonuses** and **advances** tracked
  separately against the same month.
- **Net pay computed** from all of it rather than typed in.
- **Three states**: draft, advance paid, fully paid.
- **Payment vouchers** with number and photograph of the receipt, for both advances
  and final payment.
- **Figures masked by default.** Salary, deductions and net pay show as `•••••••`
  behind a per-row reveal. The admin terminal sits where staff and guests walk
  past, and a manager opening payroll should not broadcast what everyone earns.
- **PDF export** for handing to an accountant.

## Leave

- **Requests carry** type (casual or emergency), date range, day count and reason.
- **Approval workflow** — pending, approved, declined, cancelled — so both sides
  can see what was asked and what was decided.
- **Visible to the requester**, so nobody has to ask whether their leave went
  through.

## Activity log

- **Every meaningful action is written as it happens**: room cleaned, status
  changed, item delivered, item collected, fault reported, shift started or ended.
- **Attributed to a person and a room**, with photographs where relevant.
- **Immutable** — the log is appended to, not edited.
- It is also the source the reporting view is computed from, so the report and the
  audit trail cannot disagree with each other.

## Reporting

- **Live staff status** — who is on duty right now, and since when.
- **Today's performance per person**: rooms cleaned, items delivered, items
  collected, with a points total and the day's leader highlighted.
- **Monthly performance** across the team.
- **Date-selectable daily reports** for looking back at any specific day.

## Notifications

- **Web push to staff phones** for task assignment and events needing attention,
  delivered by a dedicated worker subscribed to database changes — so a
  housekeeper does not need the app open to be reached.

## Security and access

- **Role-based access** enforced at the API, not just hidden in the interface.
- **Screenshot protection**: the interface blurs itself on `PrintScreen`, when the
  window loses focus, and when the pointer leaves the page. This is a deterrent
  against casual capture of guest details, not a defence against a determined
  attacker, and is not presented as one.
- **Hardware-bound licensing** ties an installation to a specific machine,
  validated on startup.
