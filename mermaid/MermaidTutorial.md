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
