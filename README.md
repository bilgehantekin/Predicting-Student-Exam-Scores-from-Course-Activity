Here is a detailed README that explains the workflow and each step in this notebook:

# Student Final Score Prediction

This project predicts students' final class scores using machine learning models. The workflow is implemented in the notebook `final_results.ipynb`.

## Workflow Explanation

1. **Data Loading**  
   Loads processed training and test datasets, as well as similarity and feature files for labs, quizzes, learning components, and projects.  
   - Files are read from `/kaggle/input/` and `/kaggle/working/`.

2. **Feature Merging**  
   All feature and similarity files are merged on the `UID` column to create a comprehensive feature set for each student.

3. **Combine with Train and Test Sets**  
   The merged features are joined with the train and test datasets using `UID`. Missing values are filled with zero.

4. **Feature and Target Separation**  
   - Features (`X`) are separated from the target (`FinalClass`) in the training set.
   - Test features (`X_test`) are prepared for prediction.

5. **Train/Validation Split**  
   The training data is split into training and validation sets to evaluate model performance.

6. **Model Selection**  
   Multiple regression models are available (RandomForest, XGBoost, LinearRegression, Ridge, Lasso, DecisionTree, GradientBoosting).  
   - By default, `RandomForestRegressor` is used.

7. **Model Training**  
   The selected model is trained on the training set.

8. **Validation Prediction and Evaluation**  
   - Predictions are made on the validation set.
   - Results are compared to true values.
   - Mean Squared Error (MSE) is calculated for both raw and rounded predictions.

9. **Test Prediction and Saving Results**  
   - Predictions are made for the test set.
   - Results are rounded, clipped to valid score range, and saved to `/kaggle/working/test_predicted_scores.csv`.

## Requirements

- Python 3.8+
- pandas
- scikit-learn
- xgboost

Install dependencies:
```
pip install pandas scikit-learn xgboost
```

## Usage

Run `final_results.ipynb` in your environment (Kaggle, Jupyter, PyCharm).

Outputs:
- Validation results and MSE scores printed in the notebook.
- Test predictions saved to `/kaggle/working/test_predicted_scores.csv`.

## File Structure

- `final_results.ipynb`: Main notebook for training and prediction.
- Input files: Located in `/kaggle/input/` and `/kaggle/working/`.

## Customization

- Change the model by uncommenting the desired model in the notebook.
- Adjust feature engineering or merging steps as needed.

## License

This project is for educational purposes.
