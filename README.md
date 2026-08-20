# Password Strength & Breach Checker

A command-line tool that checks password strength and cross-references it against known data breaches — without ever exposing the password itself over the network.

## Features

- **Strength scoring** — checks length, uppercase, lowercase, digits, and symbols, then rates the password Weak/Medium/Strong with specific suggestions for improvement
- **Breach checking** — checks the password against the [Have I Been Pwned](https://haveibeenpwned.com/) database of known breached passwords, using their k-anonymity API model so the actual password (or even its full hash) is never sent over the network
- **Hidden input** — password entry is not echoed to the terminal
- **Graceful failure** — handles network/API errors without crashing

## How the privacy model works

The password is hashed locally using SHA-1. Only the first 5 characters of that hash are sent to the Have I Been Pwned API, which returns all breached hashes sharing that prefix. The full match is then checked locally — so the real password never leaves your machine.

## Setup

```bash
python3 -m venv venv
source venv/bin/activate
pip3 install requests
```

## Usage

```bash
python3 password_checker.py
```

Enter a password when prompted, or type `quit` to exit.

## Built with

Python 3, using `hashlib`, `requests`, and `getpass` from the standard library plus the third-party `requests` package.
