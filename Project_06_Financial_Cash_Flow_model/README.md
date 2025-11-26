                                                    📘 Technical Documentation for Financial Cash Flow Model

This repository contains a Python-based financial model that simulates revenues, costs, taxes, CAPEX, cash flows, and calculates NPV and IRR over a 10-year horizon. It also generates visualizations for better interpretation of financial performance.

📂 Project Overview

This project provides a complete financial analysis workflow including: Revenue, cost, and CAPEX forecasting, Calculation of EBT, taxes, net cash flows, and cumulative cash flows, NPV and IRR determination


📦 Dependencies


                  🧮 Model Parameters
                  
                  The financial model uses the following assumptions:
                  Revenue growth: 5% annually
                  Cost growth: 3% annually
                  CAPEX growth: 2% annually
                  Tax rate: 25%
                  Discount rate: 10%
                  Time horizon: 10 years
                  
                  These parameters can be modified directly in the script.

🔧 Code Structure

The script is divided into several logical steps:

1. Initialization - Sets up parameters, colors, and empty lists to store computed values.
2. Cash Flow Loop,  For each year the script computes:
- Revenue
- Costs
- CAPEX
- Taxes
- Net Cash Flow
- Cumulative Cash Flow
