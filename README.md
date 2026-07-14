# AI-Powered Customer Support Analytics

Statistical analysis comparing AI chatbot and human agent performance using hypothesis testing, exploratory data analysis, machine learning, and business impact modeling.

## Executive Summary

Businesses are increasingly relying on AI-powered customer support to reduce operational costs while maintaining customer satisfaction. This project analyzes six months of customer interactions to compare AI chatbots and human agents across operational efficiency and customer experience metrics.

Using Python, statistical hypothesis testing, exploratory data analysis, machine learning, and business scenario modeling, this analysis evaluates response time, interaction cost, customer satisfaction, sentiment, and resolution performance. The results suggest that AI significantly improves efficiency while maintaining comparable customer satisfaction, though human agents continue to outperform AI in customer sentiment.

## Key Findings

| Metric | Result |
|--------|--------:|
| Average Response Time | **1.51 min (AI)** vs **7.05 min (Human)** |
| Cost per Interaction | **$3.01 (AI)** vs **$7.00 (Human)** |
| Cost Reduction | **57% lower** with AI |
| Customer Satisfaction | **3.31 (AI)** vs **3.26 (Human)** |
| Customer Sentiment | **0.30 (AI)** vs **0.40 (Human)** |
| Projected Annual Savings | **$20,621** at **75% AI adoption** |

**Bottom line:** AI significantly reduced response time and operational costs while maintaining comparable customer satisfaction. Human agents produced slightly stronger customer sentiment, and the two machine learning models tested here had limited predictive power on the available features, which suggest a hybrid support strategy, backed by better routing data, may offer the best balance between efficiency and customer experience.

## Business Question

Can AI-powered customer support reduce operational costs and improve efficiency without negatively affecting customer experience?

## Data Source

This project uses a synthetic customer support dataset representing approximately six months of customer service interactions. The dataset was designed to simulate real-world operational and customer experience metrics commonly tracked by organizations evaluating AI-powered support solutions.

The dataset contains information on:

- Customer interaction timestamps
- Support channel (AI chatbot or human agent)
- Query type
- Response time
- Resolution status
- Customer satisfaction ratings
- Customer sentiment scores
- Interaction cost
- Device type
- Customer region

The dataset was used to evaluate operational efficiency, customer experience, statistical significance, machine learning performance, and the potential financial impact of increased AI adoption.

## Feature Engineering

Several derived features and business metrics were created to support statistical analysis, machine learning, and business impact modeling.

Key engineered features included:

- **Daily interaction summaries** to evaluate trends in customer support volume and operational costs over time.
- **Daily cost calculations** for AI chatbots and human agents to compare operational expenses.
- **Customer sentiment categories** by grouping continuous sentiment scores into five interpretable levels (Negative, Slightly Negative, Neutral, Slightly Positive, and Positive).
- **AI adoption scenarios** (Current, 60%, 75%, and 90% AI utilization) to estimate future operational costs under varying levels of automation.
- **Projected savings metrics**, including daily, six-month, annual, and cumulative cost savings associated with increased AI adoption.
- **Cost difference calculations** to quantify the financial impact of AI versus human support on a per-interaction and organizational level.

These engineered features enabled both predictive modeling and business-focused analyses, allowing the project to move beyond descriptive statistics and evaluate the operational impact of AI-powered customer support.

## Exploratory Data Analysis (EDA)

Exploratory data analysis was performed to better understand customer support operations, compare AI chatbot and human agent performance, and identify patterns across operational and customer experience metrics. The analysis focused on interaction volume, response efficiency, operational costs, customer satisfaction, and customer sentiment.

### Distribution of Customer Support Interactions

Customer interactions were distributed almost evenly between AI chatbots (49.51%) and human agents (50.49%), providing a balanced dataset for comparison and minimizing bias when evaluating performance across support methods.

### Response Time Comparison

<p align="center">
  <img src="images/Average Response Time.png" width="700">
</p>

AI chatbots responded substantially faster than human agents, averaging **1.51 minutes** compared to **7.05 minutes** for human support. This represented one of the largest operational differences observed throughout the analysis.

### Interaction Cost Comparison

<p align="center">
  <img src="images/Average Interaction Cost.png" width="700">
</p>

The average cost per AI interaction was approximately **$3.01**, while human-assisted interactions averaged **$7.00**. These findings highlighted the significant cost advantage associated with AI-powered customer support.

### Daily Operational Cost

<p align="center">
  <img src="images/Average Cost Per Day.png" width="700">
</p>

Daily operational costs consistently remained lower for AI-assisted interactions, illustrating the potential financial impact of increasing AI adoption.

### Customer Sentiment

<p align="center">
  <img src="images/Customer Sentiment.png" width="700">
</p>

While satisfaction scores were comparable, customer sentiment analysis revealed that human agents generated more positive overall sentiment. This suggests that human interactions may create stronger emotional connections, particularly during more complex customer service experiences.

## Statistical Analysis

To determine whether differences between AI chatbot and human agent performance were statistically significant, a series of independent samples t-tests were conducted. Each test evaluated whether average performance differed between support methods across key operational and customer experience metrics.

The following hypotheses were tested:

- Customer Satisfaction
- Interaction Cost
- Response Time
- Customer Sentiment

### Summary of Statistical Results

| Metric | AI Mean | Human Mean | t-statistic | p-value | Conclusion |
|---------|--------:|-----------:|------------:|---------|------------|
| Customer Satisfaction | 3.31 | 3.26 | -2.60 | 0.009 | Significant |
| Interaction Cost | $3.01 | $7.00 | 131.64 | < 0.001 | Significant |
| Response Time | 1.51 min | 7.05 min | 132.35 | < 0.001 | Significant |
| Customer Sentiment | 0.299 | 0.401 | 17.34 | < 0.001 | Significant |

All four independent samples t-tests produced statistically significant results (p < 0.05). The largest practical differences were observed in response time and interaction cost, while customer satisfaction showed only a small difference in average scores despite statistical significance. Customer sentiment was significantly higher for human-assisted interactions.

## Machine Learning

To extend the statistical analysis, two Random Forest classification models were developed to evaluate how machine learning could support customer support operations.

The models focused on two practical business questions:

1. **Can we predict whether a customer interaction will require follow-up?**
2. **Can we predict whether an incoming interaction should be handled by an AI chatbot or a human agent?**

Both models were evaluated using classification metrics including accuracy, precision, recall, and F1-score. Both are exploratory: they highlight the limits of the available features for these business questions more than they provide production-ready predictions.

### Model 1: Predicting Follow-Up Requirements

The first Random Forest model predicted whether a customer interaction would require additional follow-up after the initial support session.

#### Model Performance

| Metric | Value |
|---------|------:|
| Accuracy | **81%** |
| Precision | **0.22** |
| Recall | **0.01** |
| F1-Score | **0.02** |

<p align="center">
  <img src="images/Model 1 Confusion Matrix.png" width="500">
</p>

Although the Random Forest model achieved an overall accuracy of 81%, the confusion matrix revealed that it correctly identified only 4 of 370 interactions requiring follow-up (1.1% recall). While the model performed well at identifying interactions that did not require follow-up, it was ineffective at detecting the cases most important from an operational perspective. These results suggest that the available predictor variables were not sufficient to accurately identify customers requiring additional support.

### Model 2: Predicting AI vs. Human Agent Assignment

A second Random Forest classifier was developed to predict whether an incoming customer interaction should be assigned to an AI chatbot or a human support agent based on the characteristics of the interaction.

#### Model Performance

| Metric | Result |
|---------|-------:|
| Overall Accuracy | **52%** |
| Precision (Human Agent) | **0.53** |
| Recall (Human Agent) | **0.55** |
| F1-Score (Human Agent) | **0.54** |
| Support | **1,024** |

<p align="center">
  <img src="images/Model 2 Confusion Matrix.png" width="500">
</p>

Although the second Random Forest model achieved an overall accuracy of 52%, the confusion matrix revealed that predictions were distributed nearly evenly across all four outcome categories (481, 495, 461, and 563). The model correctly identified human agent interactions slightly more often than not (563 of 1,024, approximately 55% recall), while AI chatbot interactions were correctly classified at a rate close to chance. This near-uniform distribution across the matrix indicates that the model was largely unable to distinguish between interactions best suited for AI versus human support. These results reinforce the conclusion that the available interaction characteristics were not sufficient to reliably guide automated routing decisions, and that additional features would likely be necessary to improve performance.

## Business Impact Analysis

To translate the analytical findings into actionable business insights, multiple AI adoption scenarios were modeled to estimate the financial impact of increasing automation within customer support operations.

The analysis compared current support costs with projected costs under higher levels of AI adoption while assuming customer satisfaction remained comparable to the observed results.

### AI Adoption Scenarios

<p align="center">
  <img src="images/Support Costs.png" width="1000">
</p>

Increasing AI adoption produced substantial reductions in projected support costs. While AI chatbots significantly reduced operational expenses and response times, customer satisfaction remained relatively stable, suggesting that greater automation may be implemented without negatively affecting overall service quality.

### Projected Cost Savings

<p align="center">
  <img src="images/Projected Savings.png" width="700">
</p>

The scenario analysis estimated that increasing AI utilization to 75% could reduce annual customer support costs by approximately $20,621. Higher adoption levels generated even greater long-term savings, demonstrating the financial value of strategically expanding AI-assisted customer support.

## Conclusion & Recommendations

This project evaluated whether AI-powered customer support can improve operational efficiency while maintaining a positive customer experience. Through exploratory data analysis, statistical hypothesis testing, machine learning, and business impact modeling, the findings demonstrated that AI chatbots significantly reduced response times and operational costs while maintaining customer satisfaction comparable to human agents.

Although human agents generated higher customer sentiment, the difference in customer satisfaction was minimal, suggesting that AI is well suited for handling routine customer inquiries. Machine learning models further demonstrated both the opportunities and limitations of predictive analytics within customer support operations. While predicting follow-up requirements and optimal support channel assignment remains challenging with the available data, the models identified opportunities for future improvement through additional features and more advanced modeling techniques.

### Recommendations

- Increase AI adoption for routine customer inquiries to improve operational efficiency and reduce support costs.
- Continue routing complex or emotionally sensitive interactions to human agents to preserve customer experience.
- Collect additional customer interaction features to improve predictive model performance.
- Explore advanced machine learning techniques and class balancing methods to improve follow-up prediction and automated support routing.
- Continuously monitor customer satisfaction and sentiment as AI adoption expands to ensure service quality remains high.

Overall, the analysis supports a **hybrid customer support strategy**, where AI chatbots manage high-volume routine requests while human agents focus on interactions requiring empathy, judgment, and complex problem-solving.

## Future Improvements

Several opportunities exist to extend this analysis and improve both the predictive models and business recommendations:

- **Incorporate additional customer interaction features**, such as inquiry complexity, conversation length, historical customer behavior, and text-based support transcripts to improve predictive performance.
- **Address class imbalance** in the follow-up prediction model using techniques such as SMOTE, class weighting, or oversampling to improve detection of interactions requiring additional support.
- **Evaluate additional machine learning algorithms**, including Gradient Boosting, XGBoost, and LightGBM, to compare predictive performance against the Random Forest models.
- **Develop a real-time support routing model** capable of recommending whether incoming customer interactions should be assigned to an AI chatbot or a human agent.
- **Build an interactive business intelligence dashboard** using Tableau or Power BI to monitor customer satisfaction, operational costs, response times, and AI adoption metrics.
- **Validate the analysis using real-world customer support data** to assess model performance and business impact in a production environment.

## Tools & Libraries

- **Python** — pandas, NumPy
- **Statistical analysis** — SciPy (independent samples t-tests)
- **Machine learning** — scikit-learn (Random Forest classifiers)
- **Visualization** — Matplotlib

## Repository Structure

```
├── AI_Powered_Customer_Support.ipynb   # Full analysis notebook
├── images/                             # Exported chart images used in this README
└── README.md
```

## How to Run

1. Clone the repository and install dependencies (`pandas`, `numpy`, `scipy`, `scikit-learn`, `matplotlib`).
2. Open `AI_Powered_Customer_Support.ipynb` in Jupyter Notebook or JupyterLab.
3. Run all cells to reproduce the EDA, statistical tests, machine learning models, and business impact scenarios.
