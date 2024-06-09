# Healthcare-Predictive-Analytics-for-Diseases-Diagnosis-
Healthcare predictive analytics is a rapidly evolving field that leverages data science and machine learning techniques to analyze 
historical and real-time healthcare data to make predictions about future events and trends. By identifying potential health risks, 
optimizing treatment plans, and improving patient outcomes, predictive analytics is transforming healthcare into a more efficient, 
effective, and patient-centered system. Machine learning algorithms, such as Random Forest Classifier, Logistic Regression, Decision 
Trees, and Neural Networks, are essential for building predictive models for disease detection. By analyzing patient data and 
identifying patterns associated with specific diseases, predictive models can assist in early diagnosis, enabling timely intervention 
and personalized treatment plans

from flask import Flask, render_template, request

from helper.helper import predict

import os

app=Flask(__name__)

@app.route('/')
def index():
    return render_template("index.html")


@app.route('/recommend')
def recom():
    return render_template("Recommender.html")


@app.route('/result')
def result():
    return render_template("Result.html")

@app.route('/predict',methods=["POST"])
def prediction():
    symptoms = request.get_json()["data"]
    return predict(symptoms)


if __name__ == '__main__':
    app.run(debug=False, port=os.getenv("PORT", default=5000))
