# Diagram Examples

## Flowcharts

```mermaid
graph LR
  A[Start] --> B{Failure?};
  B -->|Yes| C[Investigate...];
  C --> D[Debug];
  D --> B;
  B ---->|No| E[Success!];
```

## Sequence Diagrams

```mermaid
sequenceDiagram
  autonumber
  Server->>Terminal: Send request
  loop Health
      Terminal->>Terminal: Check for health
  end
  Note right of Terminal: System online
  Terminal-->>Server: Everything is OK
  Terminal->>Database: Request customer data
  Database-->>Terminal: Customer data
```


```mermaid
  sequenceDiagram
      participant R as Researcher
      participant P as Participant
      participant S as Scanner
  
      R->>P: Explain procedure
      P->>R: Sign consent form
      R->>S: Position participant
      S->>S: Run scanning protocol
      S->>R: Complete scan
```

```mermaid
graph LR
    A[Participant Arrival] --> B[Safety Screening]
    B --> C[Setup]
    C --> D[Scanning]
    D --> E[Post-Scan]
```