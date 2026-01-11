# 1. VECTORS + ROTATION MATRICES (baseline, no complex numbers)

## Start with a 2D vector

`v = (x, y)`

## Rotate by angle θ

You already know this matrix:

`R(θ) = | cosθ  -sinθ |        | sinθ   cosθ |`

Apply it:

`x' = x cosθ - y sinθ y' = x sinθ + y cosθ`

### Key observation

- `x'` depends on **both** `x` and `y`
    
- `y'` depends on **both** `x` and `y`
    

This is coupling.

Rotation **forces** the two values to evolve together.

---

## Time-based rotation

If the vector rotates continuously:

`θ(t) = ω · t`

Where:

- `t` = time (seconds)
    
- `ω` = angular speed (radians per second)
    

Then every frame:

`v(t) = R(ωt) · v0`

This already explains oscillation, circular motion, camera bob, sway, etc.

Nothing imaginary so far.

---

# 2. SAME THING — ENGINE-STYLE CODE

Let’s write the rotation update explicitly.

`struct Vec2 {     float x, y; };  Vec2 Rotate(Vec2 v, float theta) {     float c = cos(theta);     float s = sin(theta);      return {         v.x * c - v.y * s,         v.x * s + v.y * c     }; }`

### Notice what you **cannot** do

There is no correct way to rotate by updating only `x` or only `y`.

That restriction is the _entire point_.

---

## Continuous rotation (no trig per frame)

You can precompute a **small rotation step**:

`float c = cos(deltaTheta); float s = sin(deltaTheta);  Vec2 Step(Vec2 v) {     return {         v.x * c - v.y * s,         v.x * s + v.y * c     }; }`

This is how oscillators, springs, and filters stay stable.

---

# 3. COMPLEX NUMBERS = THIS EXACT CODE, PACKED INTO ONE TYPE

## Define a complex number

`z = x + i y`

This is just:

`(x, y)`

No magic yet.

---

## Define multiplication

Multiply by:

`r = a + i b`

Result:

`z' = (x + i y)(a + i b)    = (xa − yb) + i(xb + ya)`

Translate directly to code:

`struct Complex {     float x; // real     float y; // imaginary };  Complex Mul(Complex z, Complex r) {     return {         z.x * r.x - z.y * r.y,         z.x * r.y + z.y * r.x     }; }`

Compare this to the rotation matrix.

They are **identical**.

---

## What enforces coupling?

This rule:

> You are only allowed to update the value through complex multiplication.

There is **no legal complex operation** that:

- changes `x` without `y`
    
- changes `y` without `x`
    

The coupling is enforced by algebra, not storage.

---

## What is `i`?

Multiply by `i = (0, 1)`:

`(x, y) → (−y, x)`

That is a **90° rotation**.

Nothing imaginary is happening.

---

## What is `e^(iωt)`?

It is just this rotation packed into a function.

`e^(iθ) = cosθ + i sinθ`

So:

`e^(iωt)`

Means:

> “Rotate at ω radians per second”

No more, no less.

---

# 4. WHY `Re( C · e^(iωt) )` EVER APPEARS

Let:

- `C` = starting vector (amplitude + phase)
    
- `e^(iωt)` = rotation over time
    

Then:

`z(t) = C · e^(iωt)`

Is a rotating vector.

Taking:

`Re(z)`

Just means:

> “Project onto X if I only want one scalar”

In games, you usually **don’t do this**.  
You keep the full vector.

---

# 5. BRIDGE TO QUATERNIONS (THIS IS THE PAYOFF)

## In 2D

- Rotation axis is implicit (out of the screen)
    
- One imaginary unit (`i`) is enough
    

## In 3D

- Rotation axis matters
    
- One `i` is not enough
    

So we generalize:

|Concept|2D|3D|
|---|---|---|
|Vector|complex|quaternion|
|Rotation|multiply by `e^(iθ)`|multiply by unit quaternion|
|Coupling|enforced|enforced|
|Gimbal lock|impossible|impossible|

A quaternion is literally:

> A complex number extended to 3 axes

If complex numbers now feel mechanical instead of mystical, quaternions will too.

---

# 6. FINAL MENTAL MODEL (KEEP THIS)

- Complex numbers are **2D vectors with rotation baked in**
    
- Coupling is enforced by **allowed operations**
    
- `ω` is just angular speed
    
- `e^(iωt)` is a rotating direction
    
- Quaternions are the same idea in 3D