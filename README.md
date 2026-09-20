# Temperature-Aware SOC Estimation Dataset

This dataset contains processed lithium-ion battery discharge segments for state-of-charge (SOC) estimation under multiple temperatures and operating conditions. The measurements were collected using 18650-type LiNi0.6Co0.2Mn0.2O2 cells on a programmable battery test platform.

## File structure

```text
random/
  10C/
  15-20C/
  25C/
  30-35C/
  40C/

detailed/
  10C/
  15-20C/
  25C/
  30-35C/
  40C/
```

The `random` directory contains Staircase, Congested, Highway, and Urban current-profile families. The `detailed` directory contains US06-HWY, HWFET, REP05, EUDC, DST, ARTERIAL, UDDS, SC03, LA92, NYCC, NUREMBERG, and MANHATTAN profiles.

Each filename follows:

```text
<family>_<condition>_cycle<index>_cap<capacity>mAh[_repNN].csv
```

`repNN` appears only when cycle and capacity are identical for multiple random samples. File names do not contain internal cell or segment identifiers.

## CSV fields

| Field | Unit |
| --- | --- |
| `Current(mA)` | mA |
| `Voltage(mV)` | mV |
| `dI(mA)` | mA |
| `dV(mV)` | mV |
| `Power(W)` | W |
| `RawCapacity(mAh)` | mAh |
| `T(C)` | degC |
| `SOC` | 0--1 |

See `LICENSE.md` for reuse terms.
