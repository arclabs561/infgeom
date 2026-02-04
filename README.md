# infgeom

Information geometry primitives.

`logp` provides divergence/entropy functionals on the simplex; `infgeom` builds **geometric**
structure on top (metrics, distances, and later projections/dual connections) without mixing in
application policy.

## Quickstart

Add to your `Cargo.toml`:

```toml
[dependencies]
infgeom = "0.1"
```

Compute Rao (Fisher–Rao) and Hellinger distances on the simplex:

```rust
use infgeom::{rao_distance_categorical, hellinger};

let p = [0.70, 0.20, 0.10];
let q = [0.10, 0.20, 0.70];

let d_rao = rao_distance_categorical(&p, &q, 1e-12).unwrap();
let d_hel = hellinger(&p, &q, 1e-12).unwrap();

assert!(d_rao >= 0.0);
assert!((0.0..=1.0).contains(&d_hel));
```

Initial focus:
- Fisher–Rao / Rao distance for categorical distributions (simplex), via the sphere embedding.

Background reading:
- Frank Nielsen’s “Information geometry and divergences” portal: https://franknielsen.github.io/IG/index.html

## Examples

- `cargo run --example simplex_distances`

