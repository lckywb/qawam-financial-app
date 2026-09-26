# QAWĀM — Personal Financial Decision Assistant

Qur'an-based personal financial decision-support prototype.

## Full prototype modules

- Splash / Welcome
- Onboarding
- Financial Profile
- Financial Inventory
- Debt Register
- Transaction Ledger
- Home Dashboard
- Saya Mau Membeli...
- Need & Purpose Check
- Qawām Decision Check
- Decision Result
- Qur'anic Guidance
- Decision History
- Profile / Reset local data

## Qur'anic framework used in the prototype

- QS al-Furqān [25]:67 — Qawām, Isrāf, Iqtār
- QS al-A'rāf [7]:31 — Isrāf boundary
- QS al-Isrā' [17]:26–27 — Tabdhīr
- QS al-Baqarah [2]:280 — financial difficulty / debt context
- QS al-Baqarah [2]:282 — documentation of debt
- QS al-Mā'idah [5]:90–91 — Maysir risk context

The app presents these as Qur'anic guidance and decision-support context. It is not a fatwa engine.

## Prototype design principles

Qawām is operationalized through:
1. Condition
2. Need
3. Purpose / Proper Use
4. Proportionality
5. Financial Continuity

Decision outputs:
- Proporsional
- Pertimbangkan
- Tunda
- Data Belum Cukup

No Qawām score is used.

## Tech

Android Native / Java / AndroidX / Material Components.
Local persistence uses SharedPreferences + JSON.
