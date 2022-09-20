# Mermaid Tutorial

Let's go!

```mermaid
flowchart
  A --> B
```

If you need to export the diagram, you can use [mermaid.live](https://mermaid.live).

## Flowcharts

Used to model flows, e.g. a user interacting with your application.  

```mermaid
flowchart LR
  S[Start] --> A
  A(Enter your email address) --> B{Existing User}
  B -->|No| C(Enter name)
  C --> D{Accept conditions?}
  D -->|No| A
  D -->|Yes| E(Send email with magic link)
  B -->|Yes| E
  E --> End
```

Pros
- Faster than drawing
- Good for modeling flows
- Integrates with IDE
Disadvantage
- Not a lot of control to align the blocks

## Sequence Diagrams

Used to model flows when you have multiple participants. Visualize how 
participants communicate with each other.

```mermaid
sequenceDiagram
  autonumber
  participant Client
  participant OAuthProvider
  participant Server
  Client ->> OAuthProvider: Request access token
  activate OAuthProvider
  OAuthProvider ->> Client: Send access token
  deactivate OAuthProvider
  Client ->> Server: Request resource
  activate Server
  Server ->> OAuthProvider: Validate token
  activate OAuthProvider
  OAuthProvider ->> Server: Token valid
  deactivate OAuthProvider
  Server ->> Client: Send resource
  deactivate Server
```

## Class Diagrams

```mermaid
classDiagram
  class Order {
    +OrderStatus status
  }
  class OrderStatus {
    <<enumeration>>
    FAILED
    PENDING
    PAID
  }
  class PaymentProcessor {
    <<interface>>
    -String apiKey
    #connect(String url, JSON header)
    +processPayment(Order order) OrderStatus
  }
  class Customer {
    +String name
  }
  
  Customer <|-- PrivateCustomer
  Customer <|-- BusinessCustomer
  PaymentProcessor <|-- StripePaymentProcessor
  PaymentProcessor <|-- PaypalPaymentProcessor
  Order o-- Customer
  Car *-- Engine
  
```

* Aggregation (`o--`) is a type of relationship where it can be independent 
over its lifetime.
* Composition (`*--`) is a type of relationship where the object is not
independent over its lifetime.

## Entity Relationship Diagram

A bit more generic than the class diagram. Useful to create a model within
a domain.

```mermaid
erDiagram
  Customer ||--o{ Order : places
  Order ||--|{ LineItem: contains
  Customer {
    String id
    String name
  }
  Order {
    String id
    OrderStatus status
  }
  LineItem {
    String code
    String description
    int quantity
    int price
  }
```

* `o{` means zero or more. `||` means exactly one. 
Thus, `Customer ||--o{ Order : places` means a customer can have zero or more
Orders, and an Order has exactly one Customer.
* See here for syntax: https://mermaid-js.github.io/mermaid/#/entityRelationshipDiagram
