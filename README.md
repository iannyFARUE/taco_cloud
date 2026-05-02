# 🌮 Taco Cloud

> A full-stack web application for designing and ordering custom tacos — built with **Spring Boot 4**, **Thymeleaf**, and **Java 17**.

---

## Overview

Taco Cloud lets users build their perfect taco from scratch. Pick a wrap, pile on the protein, choose your cheese, load up the veggies, and finish it with the right sauce. Name your creation, place your order, and you're done.

This project demonstrates a clean MVC architecture on the latest Spring Boot 4 stack — from domain modelling and server-side validation all the way through to a polished, responsive UI.

---

## Screenshots

| Home | Design Your Taco | Place Your Order |
|------|-----------------|-----------------|
| Full-viewport hero with animated logo | Ingredient cards with custom checkboxes | Two-column delivery & payment form |

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Language | Java 17 |
| Framework | Spring Boot 4.0.6 |
| Web | Spring MVC |
| Templating | Thymeleaf 3.1 |
| Validation | Jakarta Bean Validation (Hibernate Validator) |
| Boilerplate reduction | Lombok |
| Build | Maven |
| Dev tooling | Spring Boot DevTools (live reload) |
| Testing | JUnit 5 · Spring MockMvc |

---

## Features

- **Taco Designer** — choose ingredients across five categories (wrap, protein, cheese, veggies, sauce) with instant visual feedback via custom-styled checkboxes
- **Named recipes** — give your taco a unique name before submitting (minimum 5 characters enforced server-side)
- **Order form** — collect delivery address and payment details with field-level validation and inline error highlighting
- **Server-side validation** — `@Valid` + Jakarta constraints on both `Taco` and `Order` domain objects; invalid submissions return the form with contextual error banners
- **Responsive UI** — CSS Grid layout, Google Fonts (Pacifico + Nunito), animated hero sections, and hover micro-interactions that work on any screen size
- **Live reload** — Spring Boot DevTools restarts the app on every save during development

---

## Project Structure

```
taco-cloud/
├── src/
│   ├── main/
│   │   ├── java/com/hexicode/taco_cloud/
│   │   │   ├── TacoCloudApplication.java       # Entry point
│   │   │   ├── controllers/
│   │   │   │   ├── HomeController.java         # GET /
│   │   │   │   ├── DesignTacoController.java   # GET/POST /design
│   │   │   │   └── OrderController.java        # GET/POST /orders
│   │   │   └── domain/
│   │   │       ├── Ingredient.java             # id, name, Type enum
│   │   │       ├── Taco.java                   # name + ingredient list
│   │   │       └── Order.java                  # delivery + payment fields
│   │   └── resources/
│   │       ├── templates/
│   │       │   ├── home.html                   # Landing page
│   │       │   ├── design.html                 # Taco builder
│   │       │   └── orderForm.html              # Checkout
│   │       └── static/
│   │           ├── styles.css                  # Global stylesheet
│   │           └── images/
│   └── test/
│       └── java/com/hexicode/taco_cloud/
│           ├── TacoCloudApplicationTests.java
│           └── controllers/HomeControllerTest.java
└── pom.xml
```

---

## Getting Started

### Prerequisites

- Java 17+
- Maven 3.9+

### Run locally

```bash
# Clone the repo
git clone https://github.com/your-username/taco-cloud.git
cd taco-cloud/taco-cloud

# Start the application
./mvnw spring-boot:run
```

Open your browser at **http://localhost:8080**

### Run tests

```bash
./mvnw test
```

---

## User Flow

```
/ (Home)
  └── /design            ← build your taco, name it, submit
        └── /orders/current  ← fill in delivery + payment details
              └── /          ← redirect back home on success
```

---

## Key Design Decisions

**Jakarta namespace migration** — Spring Boot 3+ dropped the `javax.*` namespace in favour of `jakarta.*`. All validation annotations (`@Valid`, `@NotBlank`, etc.) use the `jakarta.validation` package throughout.

**Validation at the domain layer** — constraints live on `Taco` and `Order` rather than in controller logic, keeping controllers thin and domain objects self-describing.

**Thymeleaf `th:object` scoping** — the `#fields.hasErrors('*')` validation banner is intentionally placed inside the `<form th:object>` tag, which is required for Thymeleaf's `Fields` context to resolve correctly.

**Lombok** — `@Data` and `@RequiredArgsConstructor` eliminate boilerplate getters, setters, and constructors without obscuring intent.

---

## What's Next

- [ ] Persist tacos and orders with Spring Data JPA + PostgreSQL
- [ ] User authentication with Spring Security
- [ ] REST API layer for a future React/mobile front end
- [ ] Order history page per user
- [ ] Ingredient management admin panel

---

## Author

Built by **Ian Madhara** · [LinkedIn](https://www.linkedin.com/in/ianmadhara/) · [GitHub](https://github.com/iannyFARUE)

> Built while working through *Spring in Action* (6th ed.) by Craig Walls — extended with a custom UI, Jakarta validation migration for Spring Boot 4, and a full order flow.
