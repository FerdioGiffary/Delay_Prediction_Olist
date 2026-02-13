# Risk-Aware Delivery Time Estimation in E-Commerce Using XGBoost Quantile Regression

## Project Overview

This project focuses on developing a machine learning–based delivery time estimation (ETA) model for e-commerce logistics. Unlike conventional ETA systems that primarily optimize for average prediction accuracy, **this work explicitly addresses delay risk management**, with a particular emphasis on extreme (tail) delays that drive disproportionate operational and customer impact.

The proposed approach prioritizes tail-risk control, enabling the model to deliver not only statistically accurate predictions but also outputs that are more actionable for operational decision-making.

## Business Context

Most production ETA systems are optimized using average-error metrics (e.g., MAE). While effective at improving overall accuracy, this strategy often produces overly optimistic estimates and fails to capture the risk of severe delivery delays.

As a result, operational teams lack early signals to proactively mitigate high-risk shipments, leading to increased customer dissatisfaction, higher support costs, and downstream operational inefficiencies.

## Project Objectives

- Improve delivery time estimation accuracy.
- Reduce the severity of extreme delivery delays without increasing overall late delivery rates.
- Introduce evaluation metrics that better align with operational risk and decision-making needs.

## Analytical Approach

The project follows an end-to-end data science workflow:

1. Data Preparation
- Data cleaning and validation.
- Feature selection constrained to information available at estimation time to prevent data leakage.

2. Preprocessing
- Train–test split using an 80:20 ratio.
- Frequency encoding for categorical features.
- Consistent feature transformations applied via pipelines.

3. Modeling
- Regression-based approach (not classification).
- XGBoost Quantile Regression (P94) to explicitly model tail-risk behavior.
- Asymmetric loss formulation to penalize underestimation of delivery delays more heavily.

4. Evaluation Metrics

Model performance is evaluated across both accuracy and risk dimensions:
- Estimation Accuracy
- Mean Absolute Error (MAE)
- Median prediction error
- Delay Risk Metrics
- Late delivery rate
- Mean and median late days
- P90 delay duration
- Proportion of delays exceeding 7 and 14 days

This multi-metric evaluation provides a more comprehensive view of model performance from both technical and operational perspectives.

## Key Results

Compared to the baseline (existing ETA system), the quantile regression model demonstrates:

- ~4% reduction in MAE.
- Late delivery rate remaining stable at approximately 6%.
- Meaningful reductions in delay severity, particularly in median and P90 late days reduced for around 22%.

These results indicate that improved estimation accuracy can be achieved without increasing delivery risk, while significantly reducing exposure to extreme delays.

## Business Impact Illustration

A cost simulation was conducted using industry-informed assumptions to estimate potential financial impact. This analysis is illustrative rather than causal, intended to contextualize the economic relevance of risk-aware ETA modeling.

The simulation highlights how reducing extreme delays can translate into measurable cost savings through lower compensation, reshipment, and operational handling costs.

## Prediction Application (Streamlit)

The trained model is deployed as an interactive web application using Streamlit, enabling non-technical users to access ETA predictions easily.

*Application link:*
https://olistdelivery-eta-model-dashboard-papstr7gpebbjdbejqgjce.streamlit.app/

Key features:

- Simple input interface for shipment details.
- Real-time ETA predictions.
- Clear, operationally interpretable output.

## Business Intelligence Dashboard

An interactive Tableau dashboard complements the prediction system by providing monitoring and risk analysis capabilities.

*Dashboard link:*
https://public.tableau.com/views/OlistMonitoringDashboard/Monitoring?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link

Dashboard capabilities:

- Monitoring late delivery rates and severity.
- Risk distribution analysis across regions and shipment segments.
- Identification of high-risk delivery patterns.

## Limitations

- Cost impact analysis is based on assumptions rather than actual enterprise cost data.
- Trade-off analysis is limited to the evaluated metrics within the notebook.

## Repository Structure
```
├── dataset/          # Dataset
├── notebooks/        # Analysis notebooks (main.ipynb)
├── models/           # Model artifacts and streamlit application
├── dashboard/        # Tableau dashboard project
├── README.md         # Project documentation
└── requirements.txt  # Python dependencies
```


## Tools & Technologies
- Programming Language: Python
- Libraries: Pandas, NumPy, Scikit-learn, XGBoost, Matplotlib
- Visualization: Tableau
- Deployment: Streamlit
- Environment: Jupyter Notebook
