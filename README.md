# Improving the Ranking System of Deadlock by Valve

## Project Description
This project aims to develop a machine learning model for a fairer evaluation of individual player contributions in matches of Valve's game, Deadlock. The objective is to create a ranking system that accurately reflects the real value of each player's contributions, reduces stress, and enhances player satisfaction.

---

## Problem Statement
The current ranking system, based on the ELO system or simple win-loss records, does not take into account individual player contributions in a match. This results in situations where players gain or lose points regardless of their personal performance, which can be demotivating and unfair.

### Key Problems:
- **Lack of individual utility evaluation**: There are no mechanisms to reflect a player's true contribution to a match.
- **Inadequate motivation for support players**: Supports and other roles that are not focused on kills are undervalued.
- **Rating distortion**: Players may have a high or low rating that does not accurately reflect their actual level of play.

---

## Project Objectives
- Develop a model that assesses individual player contributions based on a wide range of game metrics.
- Create a scoring system that reflects real actions and player effectiveness.
- Account for the specifics of different roles (carry, mid, support) to provide a more accurate assessment.
- Ensure transparency and fairness in the ranking system to improve player satisfaction.

---

## Approach

### Key Metric Identification
We identified the main game metrics that influence player utility:
- **KDA (Kills/Deaths/Assists)**: Total number of kills, deaths, and assists.
- **Damage Dealt**: Total damage to enemies, scaled according to match duration.
- **Damage to Objectives**: Damage to structures with specific threshold values.
- **Structures Destroyed**: Number of structures destroyed.
- **Souls Collected (Net Worth)**: Player's economic status.
- **Souls Denied**: Denying enemy resources.
- **Urns Delivered**: Special in-game item with high impact on victory.
- **Jungle Farm**: Number of neutral creeps of different types farmed.
- **Mid Boss Kill and Crystal Addition**: Key events that significantly influence match outcomes.

### Synthetic Data Generation
- Created a synthetic dataset of 10,000 records reflecting real game scenarios.
- Used statistical distributions (normal, Poisson, binomial) to generate features.
- Considered limits and thresholds for each feature.

### Machine Learning Model Development
- **Custom Decision Tree**: Developed a custom decision tree for regression tasks.
- **Gradient Boosting**: Used a Gradient Boosting Regressor model with hyperparameter tuning.
- **Role-Based Evaluation**: Added features representing player roles (carry, mid, support) and adjusted metric weights based on role.

### Model Evaluation and Optimization
- Split data into training and testing sets.
- Evaluated models using the Mean Squared Error (MSE) metric.
- Used GridSearchCV to find the optimal hyperparameters for the gradient boosting model.
- Analyzed feature importance to understand the influence of each feature on the final score.

---

## Results
- **Improved Evaluation Accuracy**: The gradient boosting model achieved a low MSE, indicating high prediction accuracy.
- **Fairness Across Roles**: Accounting for specific metrics for different roles allowed for a more accurate assessment of supports, carries, and other positions.
- **Model Interpretability**: Feature importance analysis confirmed the expected influence of metrics on the scoring.

---

## Recommendations
1. **Integrate the Model into the Game**: Test the model on real data and integrate it into the game's ranking system if results are positive.
2. **Player Feedback**: Collect feedback from players about the new system for further optimization.
3. **Further Optimization**: Continue working on the model using real data to improve its effectiveness.

---

## Conclusion
The machine learning model developed in this project provides a fairer and more accurate system for evaluating individual contributions in Valve's game, Deadlock. It considers a wide range of game metrics and the unique characteristics of different roles, which helps increase player satisfaction and encourages fair and team-oriented play. We are confident that implementing this model will benefit both players and Valve developers.

---

## How to Use the Model
1. **Data Collection**: Integrate the collection of required metrics from matches.
2. **Data Processing**: Format and preprocess the data as needed.
3. **Model Application**: Use the trained model to calculate each player's score.
4. **Rank Update**: Update the player's rank in the system based on the calculated score.
