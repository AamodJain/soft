# Different types of abstraction
**Course: Software Engineering (CS305)** <br/>
**Instructor: Balwinder Sodhi** <br/>
**Semester: January - May 2026** <br/>

## 1. Entity Abstraction

### Definition 

An **entity abstraction** models a *real-world or conceptual entity* from the **problem domain** or **solution domain**, encapsulating both **data** and the **operations that naturally belong to that entity**.

Think: *“a thing that exists and has behavior.”*


### Key Characteristics

* Represents a **noun** in the problem domain
* Has **identity and state**
* Operations are **closely related to the entity**
* High **cohesion** and intuitive boundaries



### Examples

#### Problem-domain example

```text
Student
```

* Data: rollNumber, name, program, credits
* Operations: registerCourse(), calculateGPA(), updateProfile()

#### Solution-domain example

```text
File
```

* Data: fileName, size, permissions
* Operations: open(), read(), write(), close()



### Why Entity Abstraction Is Good Design

* Mirrors how stakeholders think about the system
* Easy to understand, maintain, and extend
* Maps well to **object-oriented design**
* Encourages **information hiding**



### Common Student Mistake

Turning entities into **data-only objects** (anemic models) and putting all logic elsewhere.



### Design Quality

**Highly desirable abstraction**
This is usually the **best and most natural** abstraction type.



## 2. Action Abstraction

### Definition 

An **action abstraction** represents a **generalized operation or service** that performs a *specific kind of task*, independent of the entities it operates on.

Think: *“something that does work.”*



### Key Characteristics

* Represents a **verb**
* Focuses on **behavior**, not identity
* Often stateless (or minimally stateful)
* Groups operations of **similar purpose**



### Examples

#### Example 1: Utility-style abstraction

```text
SortService
```

* sortArray()
* sortList()
* sortFileRecords()

All operations perform **sorting**, just on different inputs.



#### Example 2: Application service

```text
AuthenticationService
```

* login()
* logout()
* validateToken()
* resetPassword()



### Where Action Abstraction Is Used

* Service layers
* Controllers
* Utility libraries
* Functional modules



### Why It’s Useful

* Promotes **reuse**
* Avoids duplicating logic across entities
* Separates *what is done* from *who owns the data*



### Design Quality

**Good abstraction when used deliberately**
Overuse can lead to “god services” if everything becomes an action.



## 3. Virtual Machine Abstraction

### Definition 

A **virtual machine abstraction** groups a set of operations that:

* Are used by a **higher-level controller**, or
* Are built upon a **lower-level set of operations**

It creates a **layered interface** that hides complexity.

Think: *“a machine built on top of another machine.”*



### Key Characteristics

* Strongly **layer-oriented**
* Defines a **contract** for higher levels
* Hides implementation details of lower levels
* Often maps to architectural layers



### Examples

#### Example 1: Operating Systems

```text
File System API
```

Built on:

* Disk blocks
* I/O drivers

Used by:

* Applications



#### Example 2: Database Abstraction

```text
Database Access Layer
```

Provides:

* insert()
* update()
* query()

Internally uses:

* SQL
* Network calls
* Connection pooling



#### Example 3: Software Frameworks

```text
Web Framework
```

Built on:

* HTTP
* Sockets

Used by:

* Controllers and services



### Why It’s Powerful

* Enables **portability**
* Supports **change isolation**
* Makes large systems manageable
* Encourages **clean architecture**



### Design Quality

**Excellent abstraction**
This is the backbone of **layered and modular systems**.



## 4. Coincidental Abstraction

### Definition 

A **coincidental abstraction** groups operations that **have no meaningful relationship**—they are packaged together purely for convenience.

Think: *“stuff we didn’t know where else to put.”*



### Key Characteristics

* No common purpose
* Low cohesion
* Hard to understand and maintain
* Often grows uncontrollably



### Examples

#### Classic bad example

```text
Utils
```

Containing:

* formatDate()
* sendEmail()
* calculateTax()
* readFile()

These operations are **unrelated**.



### Why Coincidental Abstraction Happens

* Poor domain understanding
* Time pressure
* Lack of design discipline
* “We’ll refactor later” syndrome 😄



### Why It’s Harmful

* Breaks modularity
* Increases coupling
* Makes reuse difficult
* Becomes a dumping ground



### Design Quality

**Worst form of abstraction**
Should be **avoided or refactored** as soon as possible.



## 5. Comparative Summary

| Abstraction Type | Focus               | Cohesion    | Design Quality |
| - | - | -- | -- |
| Entity           | Real-world objects  | High        | Excellent      |
| Action           | Operations/services | Medium–High | Good           |
| Virtual Machine  | Layered interfaces  | High        | Excellent      |
| Coincidental     | Convenience only    | Low         | Poor           |



## Key Takeaway

> Good abstractions reveal **intent**.
> Bad abstractions hide **confusion**.

If you can **classify an abstraction**, you usually understand **why a design is good or bad**
