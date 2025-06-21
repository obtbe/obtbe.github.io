---
layout: post
title: Linear Regression vs Logistic Regression - Understanding the Differences
date: 2022-12-15 12:00:00
categories: [statistics, regression, analysis]
---

<div class="blog-container">
  <div class="blog-content">
    <p>Data analysis often uses two tools: linear regression and logistic regression. They sound alike, but they answer different questions. This article breaks down their differences with clear examples and the math behind them, so you can choose the right one for your data.</p>

    <h2>Linear Regression: Predicting Numbers</h2>
    <p>Linear regression predicts numbers by finding a straight-line relationship between inputs and an output. Picture yourself running a lemonade stand, trying to predict daily sales based on the day’s temperature. Hotter days might mean more customers, and linear regression can model this.</p>
    <p>Imagine you track 40 days, recording temperature in degrees Fahrenheit and lemonade cups sold. On a 65°F day, you sell 120 cups, but on an 85°F day, you sell 160 cups. Linear regression creates a line that fits this pattern. The equation is:</p>
    <pre><code>Cups Sold = b0 + b1 * Temperature</code></pre>
    <p>Here, b0 is the starting point (cups sold if temperature were 0°F), and b1 is the slope (extra cups per degree). Your data might give:</p>
    <pre><code>Cups Sold = 30 + 1.5 * Temperature</code></pre>
    <p>For a 70°F day, you’d predict 30 + 1.5 * 70 = 135 cups. The math minimizes the squared differences between actual sales and the line’s predictions, called least squares. For a 65°F day with 120 cups sold, the prediction is 30 + 1.5 * 65 = 127.5 cups, so the error is 120 - 127.5 = -7.5. Square it (7.5^2 = 56.25), sum all errors across days, and adjust b0 and b1 to make the sum as small as possible.</p>
    <p>Another example: predicting a runner’s 5K time based on weekly training hours. Data from 60 runners shows 10 hours per week gives a 25-minute finish, while 15 hours gives 22 minutes. The model might be:</p>
    <pre><code>Finish Time = 30 - 0.5 * Training Hours</code></pre>
    <p>A runner training 12 hours would finish in 30 - 0.5 * 12 = 24 minutes. Linear regression works for number predictions, assuming a straight-line relationship and evenly spread errors.</p>

    <h2>Logistic Regression: Predicting Yes or No</h2>
    <p>Logistic regression predicts whether something happens, like if a moviegoer buys popcorn. It gives a probability between 0 and 1, which you can turn into yes or no. The model uses a logistic function to curve predictions into this range.</p>
    <p>Suppose a theater tracks 150 customers, noting their age and whether they bought popcorn. A 25-year-old has a 40% chance of buying, while a 50-year-old has a 75% chance. The logistic regression equation is:</p>
    <pre><code>P(Buy Popcorn) = 1 / (1 + e^(-(b0 + b1 * Age)))</code></pre>
    <p>Here, P(Buy Popcorn) is the probability, b0 is the starting point, and b1 adjusts how age affects the chance. Your data might give:</p>
    <pre><code>P(Buy Popcorn) = 1 / (1 + e^(-(-3.5 + 0.08 * Age)))</code></pre>
    <p>For a 30-year-old, calculate -3.5 + 0.08 * 30 = -1.1, so e^(-(-1.1)) = e^1.1 ≈ 3.004. Then, P(Buy Popcorn) = 1 / (1 + 3.004) ≈ 0.25, or a 25% chance. If the probability is above 0.5, predict “yes”; otherwise, “no”. The math adjusts b0 and b1 to maximize the chance the model matches actual yes-or-no choices.</p>
    <p>Another example: predicting if a plant survives based on weekly watering days. Data from 80 plants shows 2 days of watering gives a 30% survival chance, while 5 days gives 80%. The model might be:</p>
    <pre><code>P(Survive) = 1 / (1 + e^(-(-4 + 0.9 * Watering Days)))</code></pre>
    <p>A plant watered 3 days has a probability of 1 / (1 + e^(-(-4 + 0.9 * 3))) ≈ 0.43, or 43%, so predict “no”. Logistic regression fits yes-or-no outcomes like these.</p>

    <h2>How They Differ</h2>
    <p>Linear and logistic regression tackle different tasks. Here’s a breakdown:</p>
    <ul>
      <li><strong>Output</strong>: Linear regression predicts numbers, like lemonade sales or 5K times. Logistic regression predicts probabilities for yes-or-no events, like buying popcorn or plant survival.</li>
      <li><strong>Inputs</strong>: Both use numbers or categories (e.g., temperature or weekday/weekend), but logistic regression often prefers simpler inputs for clear probability curves.</li>
      <li><strong>Math</strong>: Linear regression assumes a straight line and minimizes squared errors, calculated as:</li>
      <pre><code>Error = Sum (Actual - Predicted)^2</code></pre>
      <li>Logistic regression assumes a curved relationship and maximizes the likelihood of correct yes-or-no predictions.</li>
      <li><strong>Coefficients</strong>: In linear regression, b1 shows the output change per input unit (e.g., 1.5 cups per degree). In logistic regression, b1 shifts the probability curve, affecting the odds of “yes”.</li>
    </ul>

    <h2>When to Use Each</h2>
    <p>Use linear regression for number predictions. For example, a bakery might predict muffin sales based on the day’s foot traffic. Data from 50 days shows 200 visitors yield 80 muffins sold, while 300 visitors yield 110. The model could be:</p>
    <pre><code>Muffins Sold = 20 + 0.3 * Visitors</code></pre>
    <p>For 250 visitors, predict 20 + 0.3 * 250 = 95 muffins. Or use it to estimate a house’s energy bill based on its size, like a 1,500-square-foot house costing $120 monthly.</p>
    <p>Use logistic regression for yes-or-no predictions. A pet store might predict if a customer adopts a puppy based on visit time. Data from 100 visits shows 10-minute visits have a 20% adoption chance, while 30-minute visits have a 60% chance. Or a teacher might predict if a student submits homework based on attendance, with 90% attendance giving an 85% chance.</p>
    <p>Can you use them interchangeably? Not really. Linear regression on yes-or-no data might predict nonsense, like a 1.4 probability. Logistic regression on numbers doesn’t fit since it’s built for binary outcomes. Match the model to your question: numbers for linear, yes-or-no for logistic.</p>

    <p>Both models are powerful for data analysis. Linear regression handles number predictions, and logistic regression solves yes-or-no problems. Pick the right one for your data’s question, and you’ll get clear, useful answers.</p>
  </div>
</div>

<style>
  body {
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    line-height: 1.6;
    color: #333;
    background-color: #f5f7fa;
    margin: 0;
    padding: 0;
  }

  .blog-container {
    max-width: 800px;
    margin: 40px auto;
    padding: 20px;
    background: #fff;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    border-radius: 12px;
    overflow: hidden;
  }

  .blog-content {
    padding: 30px;
  }

  .blog-content h2 {
    font-size: 1.8em;
    color: #1a73e8;
    margin-top: 30px;
    position: relative;
    padding-bottom: 10px;
  }

  .blog-content h2::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    width: 50px;
    projectors: linear-gradient(90deg, #1a73e8, transparent);
  }

  .blog-content p {
    font-size: 1.1em;
    margin: 20px 0;
    color: #444;
  }

  .blog-content p:first-of-type {
    font-style: italic;
    color: #555;
    border-left: 4px solid #1a73e8;
    padding-left: 20px;
  }

  .blog-content ul {
    margin: 20px 0;
    padding-left: 25px;
  }

  .blog-content ul li {
    margin-bottom: 10px;
    font-size: 1.1em;
    color: #444;
  }

  /* Code Block Styling for Equations */
  pre, code {
    background: #f4f4f4;
    border-radius: 6px;
    padding: 10px;
    font-family: 'Fira Code', monospace;
    font-size: 0.95em;
    display: block;
    margin: 15px 0;
    text-align: left;
  }

  /* Hover Animation for Headings */
  .blog-content h2:hover {
    color: #005bb5;
    transition: color 0.3s ease;
  }

  /* Responsive Design */
  @media (max-width: 600px) {
    .blog-container {
      margin: 20px;
      padding: 15px;
    }

    .blog-content {
      padding: 20px;
    }

    .blog-content h2 {
      font-size: 1.5em;
    }

    .blog-content p, .blog-content ul li {
      font-size: 1em;
    }

    pre, code {
      font-size: 0.9em;
    }
  }

  /* Smooth Scroll */
  html {
    scroll-behavior: smooth;
  }
</style>