# R-JAPS benchmark data

Synthetic order data calibrated to shared precooling operations for *Joint appointment and batch scheduling for shared precooling stations with farmer responses to rescheduling*.

- Join `cases.csv` to `instances.csv` by `case_id`, and `instances.csv` to `orders.csv` by `order_set_id`. Sort orders by `random_column` (1-based). Time is in minutes, quantities are in tonnes, and costs are normalised. Order-level per-minute rates already include tonnage.
- `experiment_inputs.csv` identifies planning and evaluation inputs. Cross the E5 beta levels within each day. E11 switches beta (B) and waiting-induced processing prolongation (A) on (1) or off (0).
- `scenario_seeds.csv` stores one exact PCG64 seed per uniform array. In NumPy 2.5.3 use `Generator(PCG64(int(seed_hex, 16))).random((rows, columns))`; use the declared width before selecting 1-based order or peak columns. `arrival_laws.csv` gives the mode probabilities, inverse-Beta severity parameters, peak sharing and anchoring parameters. The arrival peaks are centred at minutes 105, 215 and 315. Continuous nominal jitter uses the smaller of its listed half-width and the order's two deviation bounds.
- The main search uses seed 41 and 500 iterations. `search_seeds.csv` lists the ten-seed stability runs.
