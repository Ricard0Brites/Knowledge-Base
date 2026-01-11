---
# Class Diagram

```table-of-contents
```
## Purpose

UML class diagrams describe the **static structure** of a system: classes, their data, their behavior, and the relationships between them.

---

## Class Structure

A class is represented as a rectangle divided into **three compartments**:

```
+------------------+
| ClassName        |
+------------------+
| properties       |
+------------------+
| methods          |
+------------------+
```

### 1. Class Name (Top)

- Name of the class
    
- _Italic_ → abstract class
    

### 2. Properties / Attributes (Middle)

- Fields or member variables
    
- Syntax:
    
    ```
    visibility name : Type = default
    ```
    
- Example:
    
    ```
    - health : int = 100
    ```
    

### 3. Methods / Operations (Bottom)

- Functions or behaviors
    
- Syntax:
    
    ```
    visibility name(parameters) : ReturnType
    ```
    
- Example:
    
    ```
    + takeDamage(amount : int) : void
    ```
    

---

## Visibility Modifiers

|Symbol|Meaning|Access Scope|
|--:|---|---|
|`+`|Public|Accessible from anywhere|
|`#`|Protected|Accessible by class and subclasses|
|`-`|Private|Accessible only within the class|

Example:

```
+ move() : void
# calculateSpeed() : float
- currentSpeed : float
```

---

## Relationships Between Classes

### 1. Association

- General connection between classes
    
- No ownership implied
    
- Shown as a solid line
    

```
Player ───── Weapon
```

Optional multiplicity:

```
Player 1 ─── * Weapon
```

---

### 2. Aggregation (Weak Ownership)

- One class _has_ another
    
- Child can exist independently
    
- Hollow diamond on the owner side
    

```
Team ◇──── Player
```

---

### 3. Composition (Strong Ownership)

- One class _owns_ another
    
- Child cannot exist without parent
    
- Filled diamond on the owner side
    

```
Car ◆──── Engine
```

---

### 4. Inheritance / Generalization

- "Is-a" relationship
    
- Subclass inherits from superclass
    
- Hollow triangle pointing to parent
    

```
Enemy ───▷ Character
```

Notes:

- Subclass inherits **public and protected** members
    
- Private members are not accessible directly
    

---

### 5. Dependency

- Temporary usage (parameters, local variables, function calls)
    
- Dashed arrow
    

```
AIController - - - > PathfindingService
```

---

## Inheritance and Virtual Functions

### Inheritance

- Represented using **generalization**
    
- Base class defines shared interface/behavior
    
- Derived classes extend or specialize behavior
    

### Virtual / Abstract Methods

- Shown in _italic_ or with `{abstract}`
    
- Must be overridden in subclasses
    

Example:

```
Character
----------------
+ update() : void
+ *attack()* : void
```

Or explicitly:

```
+ attack() : void {abstract}
```

Overridden methods in subclasses may be annotated with `{override}` (optional).

---

## Static Members

- Belong to the class, not instances
    
- Underlined in UML
    

Example:

```
+ MAX_HEALTH : int
```

---

## Interfaces

### Purpose

- Define a **behavioral contract** without implementation
    
- Used when multiple unrelated classes must expose the same behavior
    
- Supports polymorphism without shared state
    

---

### Interface Structure

- Represented as a class with the `«interface»` stereotype
    
- Contains **methods only** (no properties or fields)
    
- All methods are implicitly **public**
    

Example:
```
+-----------------------------------+
|           «interface»             |
+-----------------------------------+
| + takeDamage(amount : int) : void |
+-----------------------------------+
```


### Realization (Implementing an Interface)

- A class _implements_ an interface
    
- Shown as a **dashed line** with a **hollow triangle** pointing to the interface
    

Enemy - - -▷ IDamageable

Player - - -▷ IDamageable