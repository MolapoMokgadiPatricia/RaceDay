# RaceDay Management System


## Project Overview

RaceDay is a race event management system that connects organisers and participants on one platform. The project focuses on planning the system before development by creating an Entity Relationship Diagram (ERD), a REST API endpoint plan, and a SQL database script.

The system uses role-based access, where each user is either an Organiser or a Participant.

## System Features

### Organiser

An organiser can:

* Create and manage race events.
* Create and manage event categories.
* View participant enrolments.
* Update enrolment status.
* Record race results.

### Participant

A participant can:

* Register and log in.
* Update their profile.
* Enrol in race events and categories.
* View their enrolments.
* View their race results.

## Database Design

The database contains seven related tables:

* **User** – Stores account details for organisers and participants.
* **Organiser** – Stores organiser information linked to a user account.
* **Participant** – Stores participant profile information.
* **Event** – Stores race event details.
* **Category** – Stores categories for each event.
* **Enrolment** – Links participants to events and categories.
* **Result** – Stores the official finish time and finishing position for each enrolment.

The tables are connected using primary keys and foreign keys to maintain accurate relationships between the data.

## API Features

The REST API plan includes endpoints for:

* User registration and login.
* User profile management.
* Participant profile management.
* Organiser profile management.
* Event management.
* Category management.
* Participant enrolments.
* Recording and viewing race results.

Different endpoints are protected by role-based permissions for organisers and participants.

## Project Structure

The repository contains the following files:

docs/
* |-- RaceDay.png – Entity Relationship Diagram (ERD)
* |-- RaceDay API Endpoint Plan.md – REST API endpoint plan
* |-- RaceDayDatabase.sql – SQL database script

.github/workflows/
* |-- validate-docs.yml – GitHub Actions workflow that checks the required project files.


Evidence of GitHub Action
<img width="955" height="938" alt="image" src="https://github.com/user-attachments/assets/1918dad2-820b-4061-98b8-d6c44cbaf4ae" />
<img width="1275" height="630" alt="image" src="https://github.com/user-attachments/assets/16c99b63-0500-4337-b3de-583e36b8409e" />


## How to Run the Database

1. Open SQL Server Management Studio (SSMS).
2. Open `RaceDayDatabase.sql`.
3. Run the script to create the `RaceDayDB` database.
4. The script creates all tables and inserts sample data for testing.

## GitHub Repository

Repository Link:
https://github.com/MolapoMokgadiPatricia/RaceDay.git

## Demonstration Video

YouTube Link:
https://youtu.be/UFNdUl3ubV4

## Author
**Mokgadi Patricia Molapo**

