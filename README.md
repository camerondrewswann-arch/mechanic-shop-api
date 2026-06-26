# Mechanic Shop API

A Flask REST API built with the Application Factory Pattern. This project includes blueprints, Marshmallow schemas, SQLAlchemy models, CRUD routes, tests, and a Postman collection for a mechanic shop system.

## Assignment requirements covered

- Application Factory Pattern in `app/__init__.py`
- Customer blueprint with CRUD routes
- Mechanic blueprint with CRUD routes
- Service-ticket blueprint with routes to create tickets, assign mechanics, remove mechanics, and retrieve tickets
- Marshmallow / SQLAlchemyAutoSchema schemas
- Many-to-many relationship between `ServiceTicket` and `Mechanic`
- One-to-many relationship between `Customer` and `ServiceTicket`
- Postman collection included in `postman/Mechanic_Shop_API.postman_collection.json`
- Pytest tests included in `tests/`

## Project structure

```text
mechanic_shop_api/
├── app/
│   ├── __init__.py
│   ├── extensions.py
│   ├── models.py
│   └── blueprints/
│       ├── customers/
│       │   ├── __init__.py
│       │   ├── routes.py
│       │   └── schemas.py
│       ├── mechanics/
│       │   ├── __init__.py
│       │   ├── routes.py
│       │   └── schemas.py
│       └── service_tickets/
│           ├── __init__.py
│           ├── routes.py
│           └── schemas.py
├── postman/
│   └── Mechanic_Shop_API.postman_collection.json
├── tests/
│   ├── conftest.py
│   ├── test_customers.py
│   ├── test_mechanics.py
│   └── test_service_tickets.py
├── .env.example
├── requirements.txt
└── run.py
```

## Setup

Create and activate a virtual environment:

```bash
python -m venv venv
```

Windows:

```bash
venv\Scripts\activate
```

Mac/Linux:

```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Create your `.env` file:

```bash
cp .env.example .env
```

On Windows PowerShell, use:

```powershell
copy .env.example .env
```

Initialize the database:

```bash
flask --app run.py init-db
```

Run the app:

```bash
flask --app run.py run --debug
```

The API will run at:

```text
http://127.0.0.1:5000
```

## Run tests

```bash
pytest
```

## Main endpoints

### Customers

| Method | Endpoint | Description |
|---|---|---|
| POST | `/customers/` | Create customer |
| GET | `/customers/` | Get all customers |
| GET | `/customers/<id>` | Get one customer |
| PUT | `/customers/<id>` | Update customer |
| DELETE | `/customers/<id>` | Delete customer |

### Mechanics

| Method | Endpoint | Description |
|---|---|---|
| POST | `/mechanics/` | Create mechanic |
| GET | `/mechanics/` | Get all mechanics |
| GET | `/mechanics/<id>` | Get one mechanic |
| PUT | `/mechanics/<id>` | Update mechanic |
| DELETE | `/mechanics/<id>` | Delete mechanic |

### Service Tickets

| Method | Endpoint | Description |
|---|---|---|
| POST | `/service-tickets/` | Create service ticket |
| GET | `/service-tickets/` | Get all service tickets |
| GET | `/service-tickets/<ticket_id>` | Get one service ticket |
| PUT | `/service-tickets/<ticket_id>/assign-mechanic/<mechanic_id>` | Assign mechanic to ticket |
| PUT | `/service-tickets/<ticket_id>/remove-mechanic/<mechanic_id>` | Remove mechanic from ticket |

## Example request bodies

Create a customer:

```json
{
  "name": "Jordan Driver",
  "email": "jordan@example.com",
  "phone": "555-111-2222"
}
```

Create a mechanic:

```json
{
  "name": "Alex Wrench",
  "email": "alex@example.com",
  "phone": "555-333-4444",
  "specialty": "Transmission"
}
```

Create a service ticket:

```json
{
  "description": "Oil change and tire rotation",
  "status": "open",
  "vin": "1HGCM82633A004352",
  "customer_id": 1
}
```

## Postman

Import this file into Postman:

```text
postman/Mechanic_Shop_API.postman_collection.json
```

The collection uses this variable:

```text
base_url = http://127.0.0.1:5000
```
