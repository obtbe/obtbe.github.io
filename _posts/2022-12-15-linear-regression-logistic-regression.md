---
layout: post
title: Linear Regression vs Logistic Regression - Understanding the Differences
date: 2022-12-15 12:00:00
categories: [statistics, regression, analysis]
---

<div class="article-flow">
  <div class="article-content">
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

<style scoped>
  body {
    background: #f7f7f7 !important;
    margin: 0;
    padding: 0;
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif !important;
    color: #2d3748 !important;
  }

  .article-flow {
    max-width: 600px;
    margin: 0 auto 0 calc(50% - 300px - 100px); /* Shift left by 100px */
    padding: 80px 50px;
    display: block;
  }

  .article-content {
    max-width: 600px;
    text-align: left;
  }

  .article-content h2 {
    font-size: 1.1em;
    color: #8b4513;
    margin: 50px 0 20px;
    font-weight: 600;
    position: relative;
  }

  .article-content h2::after {
    content: '';
    position: absolute;
    left: 0;
    bottom: -5px;
    width: 40px;
    height: 1px;
    background: #8b4513;
  }

  .article-content p {
    font-size: 1em;
    color: #2d3748;
    margin: 25px 0;
    line-height: 1.7;
  }

  .article-content p:first-of-type {
    font-style: italic;
    color: #4a5568;
    position: relative;
  }

  .article-content p:first-of-type::before {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    height: 100%;
    width: 2px;
    background: #8b4513;
  }

  .article-content ul {
    margin: 25px 0;
    padding-left: 20px;
    list-style: none;
  }

  .article-content ul li {
    font-size: 0.95em;
    color: #2d3748;
    margin-bottom: 12px;
    position: relative;
  }

  .article-content ul li::before {
    content: '•';
    position: absolute;
    left: -15px;
    color: #8b4513;
  }

  .article-content pre, .article-content code {
    background: #f4f4f4;
    padding: 12px;
    font-family: 'Fira Code', monospace;
    font-size: 0.95em;
    display: block;
    margin: 20px 0;
    text-align: left;
  }

  .article-content a {
    color: #8b4513;
    text-decoration: none;
    transition: color 0.3s ease;
  }

  .article-content a:hover {
    color: #5c2d0c;
  }

  /* Override styles.scss title styles */
  .post-title, h1.post-title {
    max-width: 600px !important;
    margin: 0 auto 0 calc(50% - 300px - 100px) !important; /* Shift left by 100px */
    text-align: left !important;
  }

  /* Responsive Design */
  @media (max-width: 640px) {
    .article-flow {
      max-width: 100%;
      margin: 0 0 0 100px; /* Maintain 100px left shift */
      padding: 50px 25px;
    }

    .article-content {
      max-width: 100%;
    }

    .article-content h2 {
      font-size: 1em;
    }

    .article-content p, .article-content ul li {
      font-size: 0.9em;
    }

    .article-content pre, .article-content code {
      font-size: 0.85em;
    }

    .post-title, h1.post-title {
      max-width: 100% !important;
      margin: 0 0 0 100px !important; /* Maintain 100px left shift */
    }
  }

  /* Smooth Scroll */
  html {
    scroll-behavior: smooth;
  }
</style>