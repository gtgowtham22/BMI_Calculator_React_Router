# Ex06 BMI Calculator
## Date: 26.3.2026

## AIM
To develop a responsive and interactive Body Mass Index (BMI) Calculator using React that allows users to input their height and weight, and calculates their BMI to categorize their health status (e.g., Underweight, Normal, Overweight, Obese).

## DESIGN STEPS

### STEP 1: Initialize React Project

<li>Create a new React app using create-react-app.</li>
<li>Install React Router using:</li>
npm install react-router-dom

### STEP 2: Set Up Routing

Create routing structure with react-router-dom:

<li>Home route (/) – Intro or Navigation</li>

<li>BMI Calculator route (/bmi)</li>

<li>Result route (/result)</li>

### STEP 3: Design the BMI Form Page

<li>Create a form to accept Height (in cm or m) and Weight (in kg).</li>

<li>On form submit, navigate to the result page with entered values via URL query params or context/state.</li>

## STEP 4: Handle Input Validation

<li>Check if height and weight are valid numbers.</li>

<li>Optionally, show error messages for invalid inputs.</li>

### STEP 5: Perform BMI Calculation

<li>In the result component:

<li>Extract height and weight from the route (URL or passed state).</li>

<li>Apply the BMI formula:</li>

![image](https://github.com/user-attachments/assets/ec785506-c96b-489e-8783-fb1a5d36101a)
​
 
<li>Convert height from cm to m if needed.</li></li>

### STEP 6: Display Result

<li>Show calculated BMI.</li>

<li>Show category based on BMI range:

<li>Underweight, Normal, Overweight, Obese, etc.</li></li>

### STEP 7: Navigation Options

<li>Provide a button to go back to the BMI form to calculate again.</li>

### STEP 8: Enhancements

<li>Add styling using CSS or Tailwind.</li>

## PROGRAM
```
BHI.jsx
import React, { useState } from 'react';

const Bmi = () => {
  const [weight, setWeight] = useState('');
  const [height, setHeight] = useState('');
  const [bmi, setBmi] = useState(null);
  const [message, setMessage] = useState('');

  const calculateBMI = () => {
    if (!weight || !height) {
      setMessage('Please enter valid weight and height.');
      setBmi(null);
      return;
    }

    const heightInMeters = height / 100;
    const calculatedBMI = (weight / (heightInMeters * heightInMeters)).toFixed(2);
    setBmi(calculatedBMI);

    if (calculatedBMI < 18.5) {
      setMessage('Underweight');
    } else if (calculatedBMI < 24.9) {
      setMessage('Normal');
    } else if (calculatedBMI < 29.9) {
      setMessage('Overweight');
    } else {
      setMessage('Obese');
    }
  };

  return (
    <div className="bmi-box">
        <h2  className="app-container">(BMI) Calculator</h2>
      <div className="input-group">
        <label>Weight (kg):</label>
        <input
          type="number"
          placeholder="e.g. 60"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
        />
      </div>

      <div className="input-group">
        <label>Height (cm):</label>
        <input
          type="number"
          placeholder="e.g. 170"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
        />
      </div>

      <button onClick={calculateBMI}>Calculate</button>

      {bmi && (
        <div className="result">
          <h3>Your BMI: {bmi}</h3>
          <p>Status: {message}</p>
        </div>
      )}
    </div>
  );
};

export default Bmi;
```
```
index.css
body {
  font-family: Arial, sans-serif;
  background: linear-gradient(50deg,rgb(106, 106, 210),rgb(238, 238, 106),rgb(78, 78, 224));
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;

}

.app-container {
  text-align: center;
}

.bmi-box {
  background-color: #ffffff;
  padding: 30px;
  border-radius: 12px;
  width: 320px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  margin-top: 20px;
}

.input-group {
  margin: 20px 0;
  text-align: left;
}

.input-group label {
  display: block;
  margin-bottom: 6px;
  font-weight: bold;
}

.input-group input {
  width: 100%;
  padding: 10px;
  font-size: 15px;
  border: 1px solid #ccc;
  border-radius: 8px;
}

button {
  margin-top: 15px;
  padding: 10px 25px;
  font-size: 16px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.2s ease-in-out;
}

button:hover {
  background-color: #388e3c;
}

.result {
  margin-top: 25px;
  text-align: center;
}

.result h3 {
  margin: 0;
  font-size: 24px;
}

.result p {
  font-size: 18px;
  color: #555;
}
```
## OUTPUT
<img width="1919" height="928" alt="439674712-d7e388c1-4839-45fd-80ce-62be4965fe68" src="https://github.com/user-attachments/assets/621470dd-99c4-49db-a3d5-4b14e9215b43" />




## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.
