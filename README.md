
# 🚗 Dynamic Pricing Engine for Urban Parking Lots
**Capstone Project | Summer Analytics 2025 – Consulting & Analytics Club × Pathway**

This project simulates a dynamic pricing engine for 14 urban parking spaces using real-time-like data, applying demand-sensitive pricing logic built from scratch using only `pandas`, `numpy`, and `matplotlib`.

---

## 📊 Project Summary

**Goal:** Adjust parking lot prices over time based on:
- Occupancy levels
- Queue length
- Nearby traffic conditions
- Special events
- Vehicle type

We implement two models:
- **Baseline Model:** Linear price adjustment using occupancy ratio
- **Demand-Based Model:** Multi-factor sigmoid-based pricing

---

## 🧠 Models Implemented

### 1. **Baseline Linear Model**
> Price increases proportionally with occupancy rate.

```python
new_price = prev_price + α * (occupancy / capacity)
```

- Starts at $10
- Smooth and predictable
- Lot-specific and sequential

### 2. **Demand-Based Model**
> Price adjusts using normalized demand built from multiple features.

```python
raw_demand = (
    1.0 * occupancy_rate +
    0.6 * queue_length -
    0.5 * traffic +
    0.4 * is_special_day +
    0.5 * vehicle_weight
)

normalized = sigmoid(raw_demand)
demand_price = 10 * (1 + 0.5 * norm_demand)
```

- Non-linear sigmoid-based response
- Output prices are clipped between $5 and $20
- Reflects market-like behavior

---

## 📁 Files

```
├── dataset.csv                # Input dataset (73 days × 14 lots × time slots)
├── Notebook.ipynb      # Main notebook with models and plot
├── README.md                  # Project overview and instructions
```

---

## 📈 Plot Example

The notebook includes a function:

```python
plot_prices(df, location_id='BHMBCCMKT01')
```

Which plots both Baseline and Demand-Based prices over time using `matplotlib`.

---

## ⚙️ How to Run

1. Clone this repo or open it in [Google Colab](https://colab.research.google.com/)
2. Run all cells in `Notebook.ipynb`
3. View price trends by lot ID

---

## 📌 Assumptions & Design Choices

- **Vehicle Weights:** Car=1.0, Bike=0.7, Truck=1.5
- **Traffic Mapping:** Low=1, Medium=2, High=3
- **Base Price:** $10, clipped between $5 and $20
- Used a **sigmoid function** for smoother, more realistic demand response
- No external ML libraries used (as per project requirement)

---

## ✍️ Author

**Satvik Sharma**  
[GitHub](https://github.com/Xenohhhh)

---

## ✅ Project Status

✔️ Step 1–4: Data processing and both models implemented  
✔️ Step 5: Price visualization for selected lots  
⬜ Step 6–7: (Optional) Real-time simulation with Pathway and competitive model

---

## 🏁 License

This project is part of the Summer Analytics 2025 capstone program. Open to educational use.
