[session_20_README.md](https://github.com/user-attachments/files/32117667/session_20_README.md)
# Session 20 – Python OOP: Encapsulation, Getters/Setters & Abstraction

This notebook builds on earlier OOP sessions, introducing encapsulation with "private" attributes, getter/setter methods with validation, encapsulated collections, and abstract base classes for polymorphic behavior — using e-commerce, music playlist, and payment examples.

## Contents

### 1. Private Attribute with a Display Method
Defines a `Product` class with a "private" (convention-based, single-underscore) `_price` attribute, accessed via a `display_price()` method rather than directly.

```python
class Product:
    def __init__(self, price):
        self._price = price

    def display_price(self):
        print("Product Price:", self._price)
```

**Output:** `Product Price: 999`

### 2. Getter and Setter Methods with Validation
Extends `Product` with `get_price()` and `set_price()` methods. `set_price()` validates input and raises a `ValueError` if a negative price is provided.

```python
def get_price(self):
    return self._price

def set_price(self, new_price):
    if new_price < 0:
        raise ValueError("Price cannot be negative")
    self._price = new_price
```

**Output:**
```
Original Price: 1000
Updated Price: 1200
```

### 3. Encapsulated Collection (Playlist)
Defines a `Playlist` class that manages a private list of songs (`_songs`), with `add_song()`, `remove_song()` (with a not-found check), and `get_songs()` methods.

```python
class Playlist:
    def __init__(self):
        self._songs = []

    def add_song(self, song):
        self._songs.append(song)

    def remove_song(self, song):
        if song in self._songs:
            self._songs.remove(song)
        else:
            print("Song not found")

    def get_songs(self):
        return self._songs
```

**Output:**
```
Songs: ['Tum Hi Ho', 'Kesariya', 'Chaleya']
Updated Songs: ['Tum Hi Ho', 'Chaleya']
```

### 4. Abstraction with Abstract Base Classes
Uses `abc.ABC` and `@abstractmethod` to define an abstract `PaymentMethod` class with a `pay()` method, then implements it via `UPI` and `CreditCard` subclasses — demonstrating polymorphism.

```python
from abc import ABC, abstractmethod

class PaymentMethod(ABC):
    @abstractmethod
    def pay(self, amount):
        pass

class UPI(PaymentMethod):
    def pay(self, amount):
        print(f"Processing UPI payment of ₹{amount}")

class CreditCard(PaymentMethod):
    def pay(self, amount):
        print(f"Processing Credit Card payment of ₹{amount}")
```

**Output:**
```
Processing UPI payment of ₹500
Processing Credit Card payment of ₹1500
```

## Concepts Covered
- Encapsulation using single-underscore "private" attributes
- Getter/setter methods with input validation
- Managing internal collections through controlled methods
- Abstract base classes (`ABC`, `@abstractmethod`)
- Polymorphism via subclass implementations of a shared interface

## Requirements
- Python 3.x
- Standard library only (`abc` module)

## Notes
The notebook includes several empty cells at the end, likely reserved for additional exercises or practice.
