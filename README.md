# IronLog

IronLog is a **Django-based web application** designed for **powerlifting and strength training athletes** to log workouts, track personal records (PRs), and visualize training progress over time. The application transforms raw training data—such as sets, repetitions, and loads—into meaningful performance metrics that help athletes understand and improve their training.

Rather than functioning as a simple workout log, IronLog models powerlifting-specific concepts such as the three competition lifts (squat, bench press, and deadlift), training volume, totals, and **Wilks score**, presenting this information through interactive dashboards and historical views.

This project was developed as the **Capstone Project for CS50’s Web Programming with Python and JavaScript (CS50W)**.

---

## Distinctiveness and Complexity

### Distinctiveness

This project is **substantially distinct** from all previous CS50W projects:

- It is not a social network, auction site, wiki, or e-commerce platform.
- It is a **domain-specific application** focused on powerlifting and strength training, with custom rules, metrics, and workflows.
- It introduces functionality not present in prior projects, including:
  - Automatic detection of **personal records**
  - Calculation of **training volume** over time
  - Computation of **Wilks scores** based on bodyweight and sex
  - Analytical dashboards for long-term performance tracking

Importantly, the project is not only defined by what it is *not*, but by what it *is*: a training analytics platform that helps athletes make data-driven decisions using historical workout data and sport-specific performance indicators.

---

### Complexity

The project demonstrates significant complexity beyond basic CRUD operations:

- **Advanced relational data modeling**, including relationships between:
  - `User`, `Profile`, `Workout`, `WorkoutSet`, `Exercise`, and `PersonalRecord`
- **Non-trivial backend logic**, such as:
  - Aggregation of training volume by week and month
  - Comparison of historical performances to identify new PRs
  - Calculation of strength metrics and totals
- **Dynamic frontend behavior**:
  - Integration with **Chart.js** for data visualization
  - Dashboards combining data from multiple database tables
- **Additional features**:
  - CSV export of workouts and PRs
  - Profile image uploads
  - Unit preferences (kg/lb)

Together, these elements make IronLog significantly more complex than any individual project completed earlier in the course.

---

## Project Structure and File Descriptions

Below is a detailed description of all files and directories to which I contributed code.

### Root Directory

- **`manage.py`**  
  Django’s command-line utility for administrative tasks such as running the server, applying migrations, and executing tests.

- **`requirements.txt`**  
  Lists all Python dependencies required to run the application.

---

### `fitness_project/`

The main Django project configuration directory.

- **`__init__.py`**  
  Marks the directory as a Python package.

- **`settings.py`**  
  Global project configuration, including installed apps, database setup, authentication, static files, and media configuration.

- **`urls.py`**  
  Defines the project’s root URL configuration and includes routes from the `workouts` app.

- **`asgi.py` / `wsgi.py`**  
  Entry points for asynchronous and synchronous deployment environments.

---

### `workouts/`

The core application containing the majority of the project’s logic.

- **`models.py`**  
  Defines the primary data models:
  - `Profile`: user metadata such as bodyweight, sex, units, and training level
  - `Exercise`: compound and accessory exercises
  - `Workout`: individual training sessions
  - `WorkoutSet`: individual sets (weight, reps, duration, distance)
  - `PersonalRecord`: best performances per exercise

- **`views.py`**  
  Contains backend logic for:
  - User authentication (login, logout, registration)
  - Creating and managing workouts
  - Calculating volume, PRs, and statistics
  - Preparing data for dashboards
  - Exporting workout and PR data as CSV files

- **`forms.py`**  
  Django forms used for profiles, exercises, workouts, and workout sets.

- **`urls.py`**  
  Defines all application routes, including CRUD operations, dashboards, and export endpoints.

- **`templates/workouts/`**  
  HTML templates used to render all application pages.

- **`static/workouts/`**  
  Static assets such as JavaScript and CSS files, including Chart.js integration.

- **`tests.py`**  
  Automated tests validating core models and business logic.

---

## How to Run the Application

### Prerequisites

- Python 3.10 or higher  
- `virtualenv` (recommended)  
- SQLite (included by default with Django)

### Installation and Setup

```bash
git clone https://github.com/xavieralves16/fitness_tracker.git
cd fitness_tracker
python3 -m venv venv
source venv/bin/activate        # macOS/Linux
venv\Scripts\activate           # Windows
pip install -r requirements.txt
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver

