Abacus Service

This project is a small FastAPI service built to demonstrate consistency and correctness when the same service is running on multiple instances.

The application itself is stateless. It does not keep any in-memory state. Instead, all instances read from and write to a shared Redis store. Updates to the running sum use Redis atomic increment operations, which makes concurrent writes safe without adding locks or synchronization logic in the application code.

Multiple FastAPI containers can run at the same time and still return the same correct value, no matter which instance receives the request. Docker Compose is used locally to simulate this multi-node setup with two application instances connected to a single Redis instance.

The focus of this project is simplicity, clarity, and correctness rather than production-level optimizations.

Built with Python 3.12, FastAPI, Redis, and Docker.
