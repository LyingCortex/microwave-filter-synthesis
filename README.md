# microwave-filter-synthesis

A Python library for microwave filter synthesis based on coupling matrix methods.

This package focuses on:
- Generalized Chebyshev filter approximation
- Coupling matrix synthesis (Cameron / Amari methods)
- Topology transformations (folded, arrow, wheel)
- Frequency-domain response evaluation

The library is designed for **research, education, and engineering prototyping**.

---

## Installation

```bash
pip install microwave-filter-synthesis
```
## Quick Example
```python 
import microwave_filter_synthesis as mfs
```
### 1. Define filter specification
```python 
filt = mfs.ChebyshevFilter(
    order=6,
    rl=23,
    transmission_zeros=[-2.0, -1.2, 1.5]
)
```

### 2. Synthesize polynomial prototype
```python 
spec = filt.synthesize()
```
### 3. Generate coupling matrix
```python 
cm = mfs.CameronSynthesis().synthesize(spec)
cm = mfs.folded(cm)
```
### 4. Frequency response
```python 
freq = mfs.Frequency.linspace(6e9, 7.5e9, 2001)
ntw = mfs.SParameterModel().evaluate(cm, freq)
```
