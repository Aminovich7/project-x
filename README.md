# Clinic management (project-x)

A Django web app for running a small clinic's finances: staff record consultations, surgeries and room stays, and the app works out each doctor's share and the clinic's profit, with reports for any date range.

## Features

- Custom user model with registration, login, profile update (with avatar) and logout; admin and user roles
- Doctors: create, edit, delete, with specialty
- Consultations (first visits and follow-ups), surgeries and room stays: amount, doctor's percentage, receipt number and date
- Reports per section and a combined total report, filterable by date range: income, doctor shares per doctor, expenses and clinic profit
- All pages require login (class-based generic views with `LoginRequiredMixin`)
- Django admin for all models

## Stack

Python 3.12+ · Django 6 · SQLite · Pillow · Docker

## Running with Docker

```bash
docker compose up --build
```

Then open http://localhost:8000 and sign in. To create an admin account:

```bash
docker compose exec web python manage.py createsuperuser
```

## Running without Docker

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt

python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

## Project layout

| Path | What |
|---|---|
| `accounts/` | custom user model, login, registration, profile |
| `finance/` | doctors, consultations, surgeries, rooms and the report views |
| `templates/` | page templates for each section |
| `config/` | settings and URL configuration |
