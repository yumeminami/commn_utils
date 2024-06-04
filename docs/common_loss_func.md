### Loss Function

#### Mean Squared Error (MSE)

- use: regression
- formula: $MSE = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y_i})^2$
- description: measures the average squared difference between the true values and the predicted values

---

#### Mean Absolute Error (MAE)

- use: regression
- formula: $MAE = \frac{1}{n} \sum_{i=1}^{n} |y_i - \hat{y_i}|$
- description: measures the average absolute difference between the true values and the predicted values

---

#### Cross-Entropy

- use: multi-class classification
- formula: $CE = -\frac{1}{n} \sum_{i=1}^{n} \sum_{j=1}^{m} y_{ij} \log(\hat{y_{ij}})$
- description: measures the average negative log likelihood of the true labels given the predicted probabilities

---

#### Binary Cross-Entropy

- use: binary classification
- formula: $BCE = -\frac{1}{n} \sum_{i=1}^{n} [y_i \log(\hat{y_i}) + (1 - y_i) \log(1 - \hat{y_i})]$
- description: measures the average negative log likelihood of the true labels given the predicted probabilities
