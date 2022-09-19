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
