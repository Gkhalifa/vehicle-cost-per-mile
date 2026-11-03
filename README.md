# Vehicle Cost-per-Mile Calculator

A Flask web application that works out what a car actually costs to run per mile, using real charging, fuel and repair records instead of a national average.

**Status: in progress.** Phase 1 is done. Most of the features below are planned, not built yet.

## Why

I own a used Tesla and wanted to know its real running cost per mile. Published efficiency ratings and national energy prices don't reflect one specific car, its charging habits and its repair history, so I started logging my own data.

## What works today

- **SQLite schema** (`schema.sql`) with two tables:
  - `charging_sessions`: date, kWh added, cost and odometer reading
  - `repairs`: date, description, cost, odometer reading and category
- **Database setup** (`init_db.py`) creates `tracker.db` from the schema.
- **Sample data** (`test_db.py`) inserts example charging sessions and reads them back in date order.
- **Flask app skeleton** (`app.py`) with a single running route.

## Planned

- Log entry forms and a cost-per-mile calculation from the stored records
- Vehicle lookup by VIN or year, make and model
- Public data integration: EPA fuel economy ratings, NHTSA vehicle specifications and state-level fuel and electricity prices
- Support for gasoline vehicles, normalized so gas and electric cars produce a comparable cost per mile
- A designed frontend for entering data and viewing results

## Run it

```
pip install -r requirements.txt
python init_db.py
python test_db.py
python app.py
```

Then open http://127.0.0.1:5000.

## Stack

Python, Flask, SQLite.
