<div align="center">

# 📞 CallCentre

A full-stack call-logging web application built with Django

Initiate calls between numbers, persist every call with validation, and generate per-number call-history reports

<br>

![Python](https://img.shields.io/badge/Python-3.10.10-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-4.1.6-092E20?style=for-the-badge&logo=django&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-DB-003B57?style=for-the-badge&logo=sqlite&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-Templates-E34F26?style=for-the-badge&logo=html5&logoColor=white)

</div>

<br>

## 🎯 Overview

**CallCentre** simulates the record-keeping engine behind a call centre. When a call is initiated, the app validates both phone numbers, persists a call log (caller, recipient, and timestamp), and lets users query any number to retrieve its **complete call history** — every call it placed _or_ received.

It's a compact, end-to-end demonstration of the Django request/response cycle: **routing → validation → ORM persistence → templated rendering.**

<br>

## 🌟 Key Highlights

- 🏗️ **Clean and modular architecture** — a Django project package (`CallCentre`) paired with a dedicated, reusable app (`CallLog`).
- 🔄 **End-to-end request lifecycle** — from URL routing to validation, ORM persistence, and templated rendering.
- 🔎 **Smart history lookups** — multi-field `OR` queries with Django's `Q` objects surface every call a number was part of, in either direction.
- 🛡️ **Defensive by design** — server-side validation guards the database against malformed or invalid input.
- ⚡ **Zero external setup** — runs out of the box on SQLite with a single `runserver` command.

<br>

## 🛠️ Tech Stack

| Layer         | Technology                                 |
| ------------- | ------------------------------------------ |
| **Language**  | Python 3.10.10                             |
| **Framework** | Django 4.1.6                               |
| **Database**  | SQLite3                                    |
| **Frontend**  | Django Template Language (DTL), HTML5, CSS |

<br>

## ✨ Features & Functionality

- **📲 Initiate a call** — submit a _from_ and _to_ number to create a call record.
- **🛡️ Robust server-side validation** before any data is saved:
  - rejects numbers shorter than 10 digits
  - rejects numbers containing non-numeric characters
  - guards against a number calling itself
- **💾 Persistent call log** — every valid call is auto-timestamped and stored.
- **📊 Call report generation** — look up any number and retrieve every call where it appears as the **caller or recipient**, powered by a `Q` object query.
- **💬 Instant user feedback** — validation errors surface directly to the user.
- **🔐 Django admin** — built-in admin site at `/admin/` for inspecting data.

<br>

## ⚡ Getting Started

```bash
# 1. Clone the repository
git clone https://github.com/HarshTanwar1/CallCentre.git
cd CallCentre

# 2. (Recommended) Create and activate a virtual environment
python -m venv venv
source venv/bin/activate          # Windows: venv\Scripts\activate

# 3. Install Django
pip install django==4.1.6

# 4. Apply database migrations
python manage.py migrate

# 5. (Optional) Create an admin user for /admin/
python manage.py createsuperuser

# 6. Run the development server
python manage.py runserver
```

Then open **http://127.0.0.1:8000/** in your browser — use the home page to initiate calls and the report page to look up a number's history.

<br>

## 📚 What I Learned

- 🏗️ **Structuring a Django project** — separating a project package from a reusable app and understanding how the two fit together.
- 🔀 **URL routing** — wiring routes at both the project and app level using `include()` and named routes (`{% url '...' %}`).
- ⚙️ **Function-based views** — handling `GET` and `POST` requests and reading data from `request.POST` / `request.GET`.
- 🗄️ **The Django ORM** — modeling data and persisting/querying records without writing raw SQL.
- 🔎 **Complex queries** — combining conditions across multiple fields with `Q` objects.
- ✅ **Server-side validation** — applying defensive checks with Python's `re` module and feeding errors back to the user.
- 🎨 **Templating** — rendering dynamic content with `{% if %}` / `{% for %}` and securing forms with `{% csrf_token %}`.

<br>

## 🌱 Future Improvements

- **🧾 Form handling** — migrate manual `request.POST[...]` access to Django `Form`/`ModelForm` classes for cleaner, safer validation.
- **💡 Better error UX** — replace JavaScript `alert()` popups with inline form errors and Django's `messages` framework.
- **🔁 Post/Redirect/Get** — prevent accidental re-submission on page refresh.
- **🎨 UI/UX** — adopt a CSS framework (Bootstrap/Tailwind), a shared base template, and inter-page navigation.
- **📭 Empty states** — show a "no calls found" message when a number has no history.
- **📈 Richer data model** — capture call duration, end time, and status (missed/completed).

<br>

---

<div align="center">

⭐ _If you found this project helpful or interesting, consider giving it a star!_ ⭐

</div>
