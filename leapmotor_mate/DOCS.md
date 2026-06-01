# LeapMotor Mate

Trip tracking, charge logging and remote control for Leapmotor vehicles (B10 · C10 · T03), running inside Home Assistant.

## Before you start

**Use a dedicated Leapmotor account — not the one on your phone.** The Leapmotor
cloud binds a session per device, so a second client can evict your phone (and
vice-versa). Create a separate account in the Leapmotor app and share the car
with it.

You also need the Leapmotor **app TLS certificate** (the same for everyone, it
identifies the app, not you): the files `app.crt` and `app.key`, available at
**https://github.com/markoceri/leapmotor-certs**. You upload them once in the
setup wizard.

## Setup

1. Start the add-on and open its panel (car icon in the sidebar).
2. **Step 1 — Certificate:** upload `app.crt` and `app.key` (or paste their PEM
   text).
3. **Step 2 — Login:** enter your Leapmotor account email, password and
   operation **PIN**. Your model and battery are auto-detected.

The poller then starts and data begins to appear: overview, trips, charges,
statistics and remote commands.

## Configuration

The add-on options only expose the log level:

```yaml
log_level: info
```

Everything else (polling interval, charge price, language) is configured from
the web UI under **Settings** — no YAML required.

- **Polling** — parked (default 30 s) and driving (default 10 s). Polling the
  Leapmotor cloud does **not** wake or drain the car.

## Data & persistence

The SQLite database and the uploaded certificate live in the add-on's
persistent `/data` directory, so they survive restarts and updates.

## Notes

This is an unofficial project, not affiliated with Leapmotor. It uses
reverse-engineered cloud APIs and may break if Leapmotor changes them. Use at
your own risk.

Source & full docs: https://github.com/ProtossBlaster/leapmotor-mate
