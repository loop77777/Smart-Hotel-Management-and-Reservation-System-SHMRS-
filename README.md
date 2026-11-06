# Smart Hotel Management & Reservation System (SHMRS)

A Java-based hotel management and reservation demo application that models enterprise software design principles through real-world hotel workflows such as room registration, staff handling, payment processing, booking, check-in, notifications, and file persistence.

This project is implemented as a console application and demonstrates multiple design patterns and Java capabilities in a single, easy-to-run example.

## Overview

The application simulates a luxury hotel's operational flow:

- Room inventory initialization
- Staff role assignment and duty simulation
- Hotel reservation and payment processing
- Thread-safe booking logic under concurrent access
- VIP and standard guest check-in queue handling
- Booking cancellation with rollback behavior
- File-based invoice generation and object serialization
- Observers for email/SMS notifications

## Key Features

- Room creation through a factory pattern
- Reservation handling through a service engine
- Builder-based booking creation
- DAO-based in-memory booking persistence
- Strategy-based payment methods for UPI and card payments
- Synchronization and locking for race-condition-safe room booking
- Priority-based VIP check-in queue
- File persistence using character streams, object streams, and RandomAccessFile
- Notification system using observer pattern
- Exception handling for invalid payments and unavailable rooms

## Architecture and Design Patterns

The project showcases the following software engineering concepts:

- Factory Pattern: `RoomFactory`
- Builder Pattern: `BookingBuilder`
- DAO Pattern: `BookingDAO` / `InMemoryBookingDAO`
- Strategy Pattern: `PaymentStrategy`, `UPIPaymentStrategy`, `CardPaymentStrategy`
- Observer Pattern: `NotificationObserver`, `EmailNotification`, `SMSNotification`
- Singleton Pattern: `HotelConfiguration`
- Polymorphism: `Employee`, `Manager`, `Receptionist`
- Concurrency: synchronized booking logic and thread-based simulation
- Java Streams: room filtering and sorting
- File I/O: folio generation, serialization, direct ledger access

## Project Structure

```text
src/
├── com/
│   └── hotel/
│       └── shmrs/
│           ├── builder/
│           ├── config/
│           ├── dao/
│           ├── exceptions/
│           ├── factory/
│           ├── filehandling/
│           ├── main/
│           ├── model/
│           │   ├── entity/
│           │   └── enums/
│           ├── observer/
│           ├── service/
│           └── strategy/
``` 

## Main Entry Point

```text
com.hotel.shmrs.main.SmartHotelManagementApp
```

## Prerequisites

- Java JDK 8 or newer
- A terminal or IDE such as IntelliJ IDEA or Eclipse

## How to Run

From the project root folder:

### Windows (PowerShell)

```powershell
javac -d out $(Get-ChildItem -Recurse -Filter *.java | % { $_.FullName })
java -cp out com.hotel.shmrs.main.SmartHotelManagementApp
```

### Linux / macOS

```bash
mkdir -p out
find src -name "*.java" > sources.txt
javac -d out @sources.txt
java -cp out com.hotel.shmrs.main.SmartHotelManagementApp
```

## Example Workflow Demonstrated by the App

When the app starts, it performs the following and prints output to the console:

1. Creates a hotel configuration instance
2. Registers several rooms in the inventory
3. Simulates staff roles and duties
4. Filters available rooms by price using Java streams
5. Attempts concurrent room booking on the same room from two threads
6. Simulates VIP queue-based check-in processing
7. Creates a booking for a suite and writes invoice / serialized booking data
8. Demonstrates cancellation and rollback logic

## Sample Output Highlights

```text
SMART HOTEL MANAGEMENT & RESERVATION SYSTEM (SHMRS) v3.0
Taj Luxury Residences (Bengaluru)

--- 1. Staff Polymorphism & Abstract Roles ---
[Staff: Manager Vikram Rathore] Authorizing VIP allocations and inventory audits.
[Staff: Receptionist Ananya Sen] Managing guest check-in terminal.

--- 2. Dynamic Room Search via Java 8 Streams ---
[Deluxe Room #101 | Base: ?3500.0 | Available=true]
[Premium Room #201 | Base: ?5500.0 | Available=true]
[Executive Suite #301 | Base: ?9500.0 | Available=true]

--- 3. Multi-Threaded Concurrent Booking Race on Room #201 ---
[Thread 1 SUCCESS] Booking #BK-9001 [CONFIRMED] ...
[Thread 2 FAILED] Room #201 is already occupied!
```

## Notes

This application is primarily a design-pattern and Java-concepts demonstration rather than a full production-grade hospitality system. It is ideal for understanding how enterprise-style architecture can be modeled in Java using OOP, concurrency, streams, persistence, and design patterns.

## License

This project is provided for educational and demonstration purposes.
