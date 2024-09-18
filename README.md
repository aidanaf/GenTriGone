# GenTriGone

## Project Description:

Currently, the goal of this project is to create a tool that will allow the user to estimate how the addition of a new property (residential or commerical) to their locality (e.g. neighborhood) will induce a change in variables such as how much they may pay in taxes or the current value of their home, with the hope that this tool may help residents combat gentrification.

There are a number of reasons why this is extremely difficult. In terms of project implementation, we need to deal with the fact that 1) real estate data is complex, and variales of interest such as home prices depend on factors that are both static and dynamic - e.g. the number of bedrooms or the current interest rate. 2) The information we want to provide makes this a causal inference problem - as this tool would essentially perform an intervention analysis to model changes in an existing environment ("how would this new home that is planned to be built change...") - necessitating (IMO) the use of a causal model, in this case synthetic control methods (SCMs). 3) The usefulness of the tool stems froms ability to provide insight into such changes at the local level for the user, which in terms of model building means that we'll need to implement some kind of spatial filtering mechanism, not sure how to do this at the moment.

## Prototype System:

- The Multimodal Model (MMM) is a pre-trained machine learning model that combines both static and time-series data to predict changes in key variables such as home prices, property taxes, and housing demand. The MMM takes into account broad historical patterns and general economic trends, providing a baseline prediction for how housing markets respond to various changes.

  - Static Data: Zipcode-level features such as neighborhood characteristics, zoning regulations, and proximity to amenities.
  - Time-Series Data: Historical housing prices, economic growth indicators, and tax rates over time.
  - Outputs: Predicted changes in home prices, housing supply, demand, and taxes based on user input and general trends.

- The Structural Causal Model (SCM) provides the causal reasoning necessary to perform counterfactual analysis. While the MMM generates broad predictions, the SCM localizes these predictions by taking into account the specific characteristics of the user's local area and the causal relationships between variables such as housing supply, demand, prices, and taxes.

  - Intervention Modeling: The SCM allows for the simulation of interventions (e.g., adding a new property) and estimates their causal effects on home prices and taxes.
  - Counterfactual Reasoning: By holding the present conditions constant, the SCM simulates the potential outcomes of specific changes, allowing users to ask "what if" questions about the impact of new properties or neighborhood changes.
  - Local Area Adjustments: The SCM applies adjustments to the MMM’s predictions based on localized data provided by the user (e.g., zip code, local neighborhood characteristics). The system ensures that the broad predictions from the MMM are contextually relevant to the user's area, making the results specific to the local housing market.

- User Input and Local Context: The system allows users to input key details about their local area and desired intervention. The input data informs both the MMM and SCM, ensuring that predictions and causal simulations are grounded in local conditions. This includes: Zipcode (or potentially more specific data in future iterations), characteristics of the neighborhood, such as proximity to schools, crime rates, or recent infrastructure developments.

## Prototype Workflow:

1. User Input: The user provides details such as their zipcode and any desired interventions (e.g., adding a new property).

2. MMM Prediction: The MMM generates broad predictions about changes in key variables (e.g., home prices, taxes) based on the input and its pre-trained data.

3. SCM Localization and Causal Adjustment:

- The SCM localizes the MMM’s predictions by incorporating data specific to the user’s local area.
- It also performs causal analysis, simulating how the user's intervention will propagate through the system and affect other variables (e.g., demand, prices, taxes).

4. Output: The system presents the user with predictions and counterfactual analysis about how the proposed changes will affect home prices, property taxes, and other relevant variables in their local area.

## Need2do:

## Links:

SCMs: https://www.wikiwand.com/en/articles/Synthetic_control_method
MMMs: https://www.wikiwand.com/en/articles/Multimodal_learning
