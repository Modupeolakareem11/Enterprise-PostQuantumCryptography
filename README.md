# # Enterprise Post-Quantum Cryptography Platform#

## Overview
This backend project provides a Flask-based API for the QuantumShield application, with Post-Quantum Cryptography (PQC) support implemented using the liboqs-python library. The backend demonstrates how a modern web application can integrate quantum-safe key encapsulation mechanisms for secure authentication workflows and dashboard protection.

## What Was Achieved

### 1. Flask REST API Foundation
A lightweight Flask server was implemented to expose REST endpoints for:
- Health checks
- User registration
- User login
- PQC key exchange initialization
- Dashboard security status reporting

### 2. Secure Authentication Flow
The backend supports:
- User registration with password hashing using bcrypt
- Login verification against stored credentials
- JWT-based session token generation for authenticated access
- Protected dashboard status responses

### 3. Post-Quantum Encryption Integration
The project integrates liboqs-python to implement a KEM-based workflow using the ML-KEM-768 algorithm.

Key achievements include:
- Generation of a public/private keypair for encapsulation
- Storage of session key material for backend-side decapsulation
- Encapsulation and decapsulation flow for shared secret generation
- Status reporting for secure vs. blocked key exchange events

### 4. Database Integration
The backend is connected to a MySQL database using SQLAlchemy and PyMySQL. A registration table stores usernames and hashed passwords for account management.

### 5. Frontend-Ready API Design
The API was designed to be consumed by a React-based frontend, including CORS support and JSON responses for easy integration.

## Main Backend Components

### Application Entry Point
The main implementation is in `backend/index.py`.

### Core Functional Areas
- User account registration and validation
- Password hashing and verification
- PQC key encapsulation workflow
- Secure dashboard state tracking
- JWT issuance for authenticated sessions

## API Endpoints

### Health Check
- GET `/`  
Returns a simple server status message.

### User Registration
- POST `/register`  
Accepts username and password, hashes the password, and stores the user in the database.

### PQC Initialization
- POST `/kem/init`  
Initializes a KEM session and returns a public key and mock ciphertext payload.

### User Login
- POST `/login`  
Validates credentials, performs the PQC decapsulation workflow when a ciphertext is provided, and returns a JWT and security status.

### Dashboard Status
- GET `/dashboard/status`  
Returns the current security status for a specific user or all users.

## Security Model
The backend combines traditional security mechanisms with PQC concepts:
- bcrypt for password storage
- JWT for identity management
- ML-KEM-768 for quantum-safe key exchange simulation
- Security state tracking for dashboard visibility

## Technology Stack
- Flask
- Flask-CORS
- SQLAlchemy
- PyMySQL
- PyJWT
- bcrypt
- liboqs-python (OQS)
- MySQL

## Setup Notes
To run the backend locally:
1. Install Python dependencies.
2. Ensure MySQL is running and the `quantum` database exists.
3. Import the provided SQL schema.
4. Start the Flask server.

## Achievements Summary
This backend successfully demonstrated a practical proof-of-concept for integrating post-quantum cryptography into a Flask application. It combined secure authentication, database persistence, and quantum-safe key exchange concepts into a working backend architecture suitable for further development and production hardening.

## Recommended Next Steps
- Move secrets and database credentials to environment variables
- Enable HTTPS/TLS in deployment
- Replace mock ciphertext handling with a fully validated end-to-end PQC implementation
- Add unit and integration tests
- Expand monitoring and logging for security events
