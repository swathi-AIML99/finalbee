# finalbee
Final project of IIT GHU
# Real-Time Dynamic Parking Pricing Pipeline

## 🚗 Overview

This project implements a **real-time dynamic pricing system for parking lots** using streaming data. It ingests live (or simulated) parking occupancy data, computes daily prices with multiple pricing models, and visualizes the results interactively. The system is designed for rapid experimentation and can be extended for smart city or IoT parking management applications.

---

## 🛠️ Tech Stack

- **Python 3.10+**
- **Pathway 0.7+** (real-time data streaming and processing)
- **Pandas 2.2+** (data manipulation and preprocessing)
- **Bokeh 3.4+** (interactive plotting)
- **Panel 1.4+** (dashboarding)
- **JupyterLab/Colab** (recommended for development and demonstration)

---

## 🏗️ Architecture Diagram


---

## 🔎 Project Architecture & Workflow

1. **Data Ingestion**
    - Reads parking data from a CSV file containing timestamps, occupancy, and capacity.
    - Uses Pathway's `replay_csv` to simulate real-time streaming at a configurable rate.

2. **Feature Engineering**
    - Combines date and time into a single timestamp.
    - Extracts day for daily aggregation.
    - Adds additional features (e.g., queue length, traffic, special day, vehicle type) as required by advanced models.

3. **Pricing Models**
    - **Model 1: Baseline Linear Model**
        - Formula:  
          `Price = BasePrice + α * (Max Occupancy / Capacity)`
    - **Model 2: Demand-Based Price Function**
        - Formula:  
          `Demand = α * (Max Occupancy / Capacity) + β * QueueLength - γ * Traffic + δ * IsSpecialDay + ε * VehicleTypeWeight`  
          `Price = BasePrice * (1 + λ * NormalizedDemand)`
        - Price is bounded between 0.5x and 2x the base price.

4. **Aggregation**
    - Uses tumbling daily windows to aggregate occupancy and other features.
    - Computes required statistics for each day.

5. **Visualization**
    - Interactive Bokeh plots for each pricing model.
    - Panel dashboard displays real-time price evolution.

6. **Execution**
    - The entire pipeline runs in real-time, updating dashboards as new data arrives.

---

## 🚀 Getting Started

### Prerequisites

- Python 3.10 or higher
- pip

### Installation


### Running the Project

1. Place your CSV data in the project directory.
2. Update the file path in the code if necessary.
3. Run the main notebook or script.
4. Access the dashboard via the provided Panel link.

---

## 📊 Data

- **Input:** CSV with columns: `LastUpdatedDate`, `LastUpdatedTime`, `Occupancy`, `Capacity`
- **Simulated Features:** `QueueLength`, `Traffic`, `IsSpecialDay`, `VehicleTypeWeight` (replace with real data as available)

---

## 📁 Code Structure

- `main.ipynb` or `main.py` — Main pipeline and dashboard
- `parking_stream.csv` — Processed CSV for streaming
- `README.md` — Project documentation

---

## 📈 Results & Evaluation

- Real-time dashboard shows daily price evolution for both models.
- Pricing logic can be easily modified for further experimentation.
- System can be extended for more complex models or additional data sources.

---

## 🔮 Future Work

- Integrate real-time IoT data feeds.
- Add more sophisticated machine learning models.
- Deploy as a cloud-based microservice.
- Extend dashboard with more analytics and controls.

---

## 📄 License

[MIT License](LICENSE)

---

## 🙏 Acknowledgments

- Inspired by open-source smart city and data streaming projects.
- Thanks to the Pathway, Bokeh, and Panel communities for their libraries and support.

---

**How to use the diagram:**  
Copy the Mermaid code block into [Mermaid Live Editor](https://mermaid.live/) to view or export the architecture diagram.

**Tip:**  
Replace simulated feature values with real data for production use.  
For questions or contributions, open an issue or pull request on this repository!
