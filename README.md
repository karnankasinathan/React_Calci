# Ex04 Simple Calculator - React Project


## AIM
To  develop a Simple Calculator using React.js with clean and responsive design, ensuring a smooth user experience across different screen sizes.

## ALGORITHM
### STEP 1
Create a React App.

### STEP 2
Open a terminal and run:
  <ul><li>npx create-react-app simple-calculator</li>
  <li>cd simple-calculator</li>
  <li>npm start</li></ul>

### STEP 3
Inside the src/ folder, create a new file Calculator.js and define the basic structure.

### STEP 4
Plan the UI: Display screen, number buttons (0-9), operators (+, -, *, /), clear (C), and equal (=).

### STEP 5
Create a new file Calculator.css in src/ and add the styling.

### STEP 6
Open src/App.js and modify it.

### STEP 7
Start the development server.
  npm start

### STEP 8
Open http://localhost:3000/ in the browser.

### STEP 9
Test the calculator by entering numbers and operations.

### STEP 10
Fix styling issues and refine content placement.

### STEP 11
Deploy the website.

### STEP 12
Upload to GitHub Pages for free hosting.

## PROGRAM
### Calc.jsx:
```
import React, { useState } from 'react';
import './Calc.css';

const Calc = () => {
  const [input, setInput] = useState('');

  const handleClick = (value) => setInput(input + value);
  const handleClear = () => setInput('');
  const handleBackspace = () => setInput(input.slice(0, -1));

  const handleEqual = () => {
    try {
      const result = evaluateExpression(input);
      setInput(result.toString());
    } catch {
      setInput('Error');
    }
  };

  const evaluateExpression = (expr) => {
    const operators = ['+', '-', '*', '/'];
    let numbers = [];
    let currentNum = '';

    for (let char of expr) {
      if (operators.includes(char)) {
        if (currentNum) numbers.push(parseFloat(currentNum));
        numbers.push(char);
        currentNum = '';
      } else {
        currentNum += char;
      }
    }
    if (currentNum) numbers.push(parseFloat(currentNum));

    // Multiplication and division first
    for (let i = 1; i < numbers.length - 1; i++) {
      if (numbers[i] === '*' || numbers[i] === '/') {
        const left = numbers[i - 1];
        const right = numbers[i + 1];
        const result = numbers[i] === '*' ? left * right : left / right;
        numbers.splice(i - 1, 3, result);
        i--;
      }
    }

    // Addition and subtraction
    let result = numbers[0];
    for (let i = 1; i < numbers.length; i += 2) {
      const operator = numbers[i];
      const value = numbers[i + 1];
      result = operator === '+' ? result + value : result - value;
    }

    return result;
  };

  return (
    <div className="calculator">
      <div className="display">{input || '0'}</div>
      <div className="buttons">
        <button onClick={handleClear} className="clear">C</button>
        <button onClick={handleBackspace} className="backspace">⌫</button>
        <button onClick={() => handleClick('/')} className="operator">/</button>
        <button onClick={() => handleClick('*')} className="operator">*</button>

        <button onClick={() => handleClick('7')}>7</button>
        <button onClick={() => handleClick('8')}>8</button>
        <button onClick={() => handleClick('9')}>9</button>
        <button onClick={() => handleClick('+')} className="operator">+</button>

        <button onClick={() => handleClick('4')}>4</button>
        <button onClick={() => handleClick('5')}>5</button>
        <button onClick={() => handleClick('6')}>6</button>
        <button onClick={() => handleClick('-')} className="operator">-</button>

        <button onClick={() => handleClick('1')}>1</button>
        <button onClick={() => handleClick('2')}>2</button>
        <button onClick={() => handleClick('3')}>3</button>
        <button onClick={handleEqual} className="equal">=</button>

        <button onClick={() => handleClick('0')} className="zero">0</button>
        <button onClick={() => handleClick('00')} className="zero">00</button>
        <button onClick={() => handleClick('.')}>.</button>
      </div>
      <footer className="footer">
        <p>&copy; 2025 Austin Aro A (212224040038)</p>
      </footer>
    </div>
  );
};

export default Calc;
```

### Calc.css:
```
.calculator {
  width: 100%;
  max-width: 360px;
  margin: 50px auto;
  padding: 30px;
  border-radius: 16px;
  background: #1e1f26;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.7);
  color: #fff;
  font-family: 'Segoe UI', sans-serif;
}

.display {
  font-size: 36px;
  padding: 25px;
  text-align: right;
  background: #2c2d36;
  margin-bottom: 20px;
  border-radius: 10px;
  border: none;
  color: #00ffcc;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 12px;
}

button {
  padding: 22px;
  font-size: 20px;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  transition: transform 0.1s, background 0.2s;
  background-color: #3a3b47;
  color: #fff;
}

button:hover {
  transform: translateY(-2px);
  background-color: #50515e;
}

.operator {
  background-color: #ff9500;
  color: white;
}

.operator:hover {
  background-color: #cc7a00;
}

.clear {
  background-color: #ff3b30;
  color: white;
}

.clear:hover {
  background-color: #c1271c;
}

.equal {
  background-color: #34c759;
  color: white;
  grid-row: span 2;
}

.equal:hover {
  background-color: #28a745;
}

.zero {
  grid-column: span 2;
}

.footer {
  text-align: center;
  margin-top: 25px;
  font-size: 14px;
  color: #aaa;
}
```

## OUTPUT

 <img width="1255" height="652" alt="image" src="https://github.com/user-attachments/assets/6e161f75-7fdc-433d-b555-6bb9df87c26c" />


## RESULT
The program for developing a simple calculator in React.js is executed successfully.
