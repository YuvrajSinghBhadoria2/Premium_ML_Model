# Premium Insurance Predictor

This project predicts insurance premium categories based on user demographics and lifestyle factors using machine learning. It consists of a FastAPI backend for predictions, a Streamlit frontend for user interaction, and a trained ML model.

## Project Structure

```
.
├── app.py              # FastAPI backend server
├── frontened.py        # Streamlit frontend application
├── insurance.csv       # Dataset used for training the model
├── ml_model.ipynb      # Jupyter notebook with model training process
├── model.pkl           # Pre-trained machine learning model
└── README.md           # This file
```

## Features

- Predicts insurance premium categories (Low, Medium, High) based on user inputs
- Considers factors like age, BMI, lifestyle risks, city tier, income, and occupation
- RESTful API endpoint for integration with other services
- User-friendly web interface built with Streamlit

## How It Works

The machine learning model analyzes the following user inputs to predict premium categories:

1. **Age** - User's age affects risk assessment
2. **BMI** - Calculated from weight and height (Body Mass Index)
3. **Lifestyle Risk** - Based on smoking habits and BMI
4. **City Tier** - Classification of cities based on economic factors
5. **Income** - Annual income in Lakhs Per Annum (LPA)
6. **Occupation** - Job type affecting risk profile

## Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd Premium_predict_model
   ```

2. Install required packages:
   ```bash
   pip install fastapi uvicorn streamlit pandas scikit-learn pydantic requests
   ```

## Running the Application

1. **Start the FastAPI server:**
   ```bash
   uvicorn app:app --reload
   ```
   The API will be available at `http://localhost:8000`

2. **In a new terminal, run the Streamlit frontend:**
   ```bash
   streamlit run frontened.py
   ```
   The web interface will open in your browser

## API Endpoints

- `POST /predict` - Predict insurance premium category
  - **Request Body:**
    ```json
    {
      "age": 35,
      "weight": 70.5,
      "height": 1.75,
      "income_lpa": 15.0,
      "smoker": false,
      "city": "Mumbai",
      "occupation": "private_job"
    }
    ```
  - **Response:**
    ```json
    {
      "predicted_category": "Medium"
    }
    ```

## Model Training

The model was trained using a Random Forest classifier with the following features:
- Age group (young, adult, middle_aged, senior)
- Lifestyle risk (low, medium, high)
- City tier (1, 2, 3)
- Occupation type
- BMI
- Annual income

See [ml_model.ipynb](ml_model.ipynb) for detailed training process and evaluation metrics.

## Data

The [insurance.csv](insurance.csv) file contains anonymized insurance data used to train the model, with the following columns:
- age
- weight
- height
- income_lpa (Lakhs Per Annum)
- smoker
- city
- occupation
- insurance_premium_category (target variable: Low, Medium, High)

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.
