Here is the explanation in the simplest terms possible, followed by the diagram you asked for.

### The Objective in Simple Terms: "The Master Key"

We are building a security system that works like **Key Cards** in a secure office building.

1.  **The "Nation" User (The CEO):** They have a **Master Key**.
    *   **Navigation:** They see *every* door (Dashboard link).
    *   **Data Override:** They can open *any* file cabinet. We are **overriding** the rule that says "you can only see your own data." If they are in the Nation group, the system ignores the region filters and shows them **everything**.

2.  **The "Region" User (The Branch Manager):** They have a **Standard Key**.
    *   **Navigation:** They see most doors, but the "Executive Suite" (Customer 360) is invisible to them.
    *   **Data:** They can only open file cabinets labeled for their specific Region (e.g., "East").

3.  **The "Territory" User (The Junior Rep):** They have a **Restricted Key**.
    *   **Navigation:** They only see the cafeteria and their own desk (Basic dashboards).
    *   **Data:** They can strictly see only their own small slice of data (e.g., "New York City").

---

### The Mermaid Diagram: Logic Flow & Output

This diagram illustrates exactly what happens when each user logs in. Notice how the **Nation User** path bypasses the filtering logic ("The Override").

```mermaid
flowchart TD
    %% Define Styles
    classDef nation fill:#d1e7dd,stroke:#0f5132,stroke-width:2px;
    classDef region fill:#fff3cd,stroke:#856404,stroke-width:2px;
    classDef terr fill:#f8d7da,stroke:#842029,stroke-width:2px;
    classDef hidden fill:#e2e3e5,stroke:#6c757d,stroke-dasharray: 5 5,color:#6c757d;

    %% User Inputs
    subgraph Users [" USER GROUPS "]
        N_User([🟢 Nation User]):::nation
        R_User([🟡 Region User]):::region
        T_User([🔴 Territory User]):::terr
    end

    %% Logic Layer
    subgraph Logic [" SYSTEM LOGIC "]
        NavCheck{Check Group<br/>Permission}
        DataCheck{Check Data<br/>Rule}
    end

    %% Connections to Logic
    N_User --> NavCheck
    R_User --> NavCheck
    T_User --> NavCheck
    
    NavCheck --> DataCheck

    %% NATION OUTPUT
    subgraph NationOutput [" 🟢 NATION USER EXPERIENCE "]
        direction TB
        N_Nav[<b>NAVIGATION BAR</b><br/>[Link] Landing Page<br/>[Link] Digital Marketing<br/>[Link] Rep Activity<br/>[Link] Customer 360<br/>[Link] Campaign Perf<br/>[Link] Other Dash 1 & 2]:::nation
        N_Data[<b>DATA VISIBILITY</b><br/>SCOPE: 100% Full Data<br/>(Override Enabled)]:::nation
    end

    %% REGION OUTPUT
    subgraph RegionOutput [" 🟡 REGION USER EXPERIENCE "]
        direction TB
        R_Nav[<b>NAVIGATION BAR</b><br/>[Link] Landing Page<br/>[Link] Digital Marketing<br/>[Link] Rep Activity<br/>[Link] Other Dash 1 & 2<br/><span style='text-decoration:line-through'>[HIDDEN] Customer 360</span><br/><span style='text-decoration:line-through'>[HIDDEN] Campaign Perf</span>]:::region
        R_Data[<b>DATA VISIBILITY</b><br/>SCOPE: Regional Data Only<br/>(e.g., Just 'East' rows)]:::region
    end

    %% TERRITORY OUTPUT
    subgraph TerritoryOutput [" 🔴 TERRITORY USER EXPERIENCE "]
        direction TB
        T_Nav[<b>NAVIGATION BAR</b><br/>[Link] Landing Page<br/>[Link] Digital Marketing<br/>[Link] Rep Activity<br/><span style='text-decoration:line-through'>[HIDDEN] Customer 360</span><br/><span style='text-decoration:line-through'>[HIDDEN] Campaign Perf</span><br/><span style='text-decoration:line-through'>[HIDDEN] Other Dash 1 & 2</span>]:::terr
        T_Data[<b>DATA VISIBILITY</b><br/>SCOPE: Territory Data Only<br/>(e.g., Just 'New York' rows)]:::terr
    end

    %% Final Mapping
    DataCheck -- "If Nation" --> N_Nav
    N_Nav --- N_Data
    
    DataCheck -- "If Region" --> R_Nav
    R_Nav --- R_Data
    
    DataCheck -- "If Territory" --> T_Nav
    T_Nav --- T_Data
```
