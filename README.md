# 🎬 MoviWebApp

MoviWebApp is a simple Flask-based web application that allows users to manage a personalized list of movies. Users can add, view, update, and delete movies — either manually or by fetching data from the OMDb API.

---

## Features

- Add users
- Add movies manually with title, genre, year, rating
- Add movies via OMDb API using title
- Edit movie titles
- Delete movies
- View movie posters, director, and runtime
- Flash messages for actions
- Responsive design using Flexbox
- Error handling for 404 & 500
- SQLite database via SQLAlchemy ORM

---

## Project Structure

```
MoviWebApp/
│
├── app.py                  # Main Flask application
├── models.py               # SQLAlchemy models
├── data_manager.py         # Data handling and OMDb API integration
├── .env                    # Environment variables (API key, secret)
├── requirements.txt        # Python dependencies
│
├── data/
│   └── movies.db           # SQLite database (auto-created)
│
├── static/
│   └── style.css           # Custom CSS styles
│
├── templates/
│   ├── base.html           # Base template with navbar
│   ├── home.html           # Homepage to add/view users
│   ├── movies.html         # Movies page per user
│   └── errors/
│       ├── 404.html        # Not Found error page
│       └── 500.html        # Internal Server Error page
```

---

## ⚙️ Setup Instructions

### 1️. Clone the Repository

```bash
git clone https://github.com/tabeaerkelenz/moviwebapp.git
cd moviwebapp
```

### 2. Create Virtual Environment (Optional but recommended)

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Requirements

```bash
pip install -r requirements.txt
```

### 4. Set up `.env` file

Create a `.env` file in the root directory:

```env
OMDB_API_KEY=your_omdb_api_key_here
SECRET_KEY=your_flask_secret_key
```

### 5. Run the App

```bash
python3 app.py
```

Then open your browser at:  
-> `http://localhost:5000` or the provided Codio URL

---

## 🛠️ Database Initialization (first time only)

Inside `app.py`, **uncomment** the following line for the first run:

```python
with app.app_context():
    db.create_all()
```

Then run the app to create the database. After that, **comment it out again**.

Alternatively, create a one-time script `init_db.py`:

```python
from app import app, db

with app.app_context():
    db.create_all()
    print("Database and tables created.")
```

Run with:

```bash
python3 init_db.py
```

---

## Example .env File

```env
OMDB_API_KEY=12345678abcd
SECRET_KEY=supersecret123
```

---

## Styling

- The app uses a custom CSS file at `static/style.css`
- Includes:
  - Flexbox layout
  - Styled movie cards
  - Responsive poster display
  - Flash message color feedback

---

## ❗ Error Handling

- `404.html` for missing pages
- `500.html` for server errors
- All errors are routed through Flask’s `@app.errorhandler` decorators.

---

## Requirements

- Python 3.7+
- Flask
- Flask-SQLAlchemy
- requests
- python-dotenv

Install them via:

```bash
pip install -r requirements.txt
```

---

## License

MIT License
