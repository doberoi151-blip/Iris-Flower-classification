Iris Flower Classification
A supervised machine learning project that explores the Iris flower dataset and compares three classification algorithms: Logistic Regression, K-Nearest Neighbors (KNN), and Gaussian Naive Bayes.
 * Project Overview
This project uses measurements of Iris flowers to classify each sample into one of three species:
- Iris-setosa
- Iris-versicolor
- Iris-virginica
The work is implemented in a Jupyter Notebook (iris_flower.ipynb) using Pandas and Scikit-learn. The notebook loads the dataset, encodes the target labels, creates a train-test split, trains three classifiers, and prints classification metrics and confusion matrices.
Project status: Notebook-based learning/project implementation. No web application, API, or deployment is included in the supplied notebook.

 *Objectives
- Load and inspect the Iris dataset with Pandas.
- Convert categorical species labels into numeric labels.
- Split the data into training and testing subsets.
- Train and compare three classification algorithms.
- Examine accuracy, precision, recall, F1-score, and confusion matrices.
   *Technologies Used
Technology	Purpose
Python	Programming language
Jupyter Notebook	Interactive development
Pandas	Dataset loading and inspection
Scikit-learn	Label encoding, data splitting, model training, and evaluation


* Repository Structure
The following is the expected minimal structure based on the supplied notebook. Keep iris.csv in the same directory as the notebook unless you update the path in the loading cell.
iris-flower-classification/
├── iris_flower.ipynb
├── iris.csv
└── README.md
iris.csv was referenced by the notebook but was not included in the uploaded file. Add the dataset file to the repository or update the notebook to use its actual location.

* Dataset Information
The notebook reads a CSV file named iris.csv:
df = pd.read_csv("iris.csv")
The columns visible in the notebook output are:
Column	Description
Id	Row/sample identifier
SepalLengthCm	Sepal length in centimeters
SepalWidthCm	Sepal width in centimeters
PetalLengthCm	Petal length in centimeters
PetalWidthCm	Petal width in centimeters
Species	Target flower species


The notebook output shows 150 samples, with 50 samples represented in each of the three species classes. The dataset's download source and license were not specified in the supplied notebook.
⚙️ Workflow
1. Load data: Read iris.csv into a Pandas DataFrame.
2. Inspect samples: Display the first rows and a random sample.
3. Encode labels: Apply Scikit-learn's LabelEncoder to the Species column.
4. Split data: Separate features (X) and target (y), then use train_test_split with test_size=0.5 and random_state=42.
5. Train models: Fit Logistic Regression, KNN, and Gaussian Naive Bayes on the training subset.
6. Evaluate: Generate predictions and print accuracy, confusion matrices, and classification reports.


* Machine Learning Models
1. Logistic Regression
Implemented using sklearn.linear_model.LogisticRegression with max_iter=1000.
2. K-Nearest Neighbors (KNN)
Implemented using sklearn.neighbors.KNeighborsClassifier with n_neighbors=5.
3. Gaussian Naive Bayes
Implemented using sklearn.naive_bayes.GaussianNB.

* Installation and Setup
Prerequisites
- Python 3
- pip
- Jupyter Notebook or JupyterLab
- The iris.csv dataset file
1. Clone the repository
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd iris-flower-classification
Replace <YOUR_GITHUB_REPOSITORY_URL> with the actual repository URL.
2. Create and activate a virtual environment (recommended)
Windows PowerShell:
python -m venv .venv
.venv\Scripts\Activate.ps1
macOS / Linux:
python3 -m venv .venv
source .venv/bin/activate
3. Install dependencies
pip install pandas scikit-learn jupyter
4. Launch Jupyter Notebook
jupyter notebook
Open iris_flower.ipynb and run the cells in order.


* Results
The notebook currently prints the following scores:
Model	Printed accuracy
Logistic Regression	1.0000 (100.00%)
KNN	0.9933 (99.33%)
Gaussian Naive Bayes	0.9933 (99.33%)


* Evaluation note
These values are not valid held-out test-set accuracy scores. Although the notebook creates X_train, X_test, y_train, and y_test, its evaluation loop uses:
y_pred = model.predict(X)
accuracy_score(y, y_pred)
This predicts on the complete dataset, including the samples used to fit each model. Therefore, the values above describe predictions on the full dataset and should not be presented as unbiased test performance.

The notebook also includes the Id column in X, so the identifier is currently passed to the classifiers as a feature. Consider excluding it from model features.
Recommended evaluation correction
To evaluate on the held-out test set, change the prediction and metric calculations to use X_test and y_test:
for name, model in models.items():
    y_pred = model.predict(X_test)

    print(f"\n{name}")
    print("Accuracy:", accuracy_score(y_test, y_pred))
    print("Confusion matrix:")
    print(confusion_matrix(y_test, y_pred))
    print("Classification report:")
    print(classification_report(y_test, y_pred))
For a cleaner feature set, create X without the identifier column:
X = df.drop(columns=["Species", "Id"])
y = df["Species"]
After making these changes, rerun the notebook and update the results table with the newly measured test-set metrics. Do not assume the scores will remain the same.

* Possible Future Improvements
- Exclude the Id column from model training.
- Evaluate models only on the held-out test set.
- Compare models using cross-validation.
- Add exploratory data analysis and visualizations.
- Add feature scaling where appropriate and compare its effect.
- Save a fitted model and demonstrate prediction on a new flower sample.
- Add a requirements.txt file for reproducible setup.
These are suggestions for future work; they are not claimed as completed features.

  * Learning Outcomes
This notebook provides practice with:
- Loading tabular data using Pandas.
- Encoding categorical target labels.
- Splitting data into training and testing subsets.
- Fitting multiple Scikit-learn classifiers.
- Reading classification reports and confusion matrices.
- Understanding why evaluation must be performed on unseen test data.
👤 Author
Dev Srivastava
