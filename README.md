  Example Flow:

  1. You run: /prompt "create a machine learning model for anomaly detection"
  2. prompt.md reads the next.md template
  3. It replaces $ARGUMENTS with your specific task
  4. Outputs a complete, ready-to-use prompt

  Why This Design?

  - Modularity: next.md stays clean as a reusable template
  - Flexibility: prompt.md can customize the output based on your specific task
  - Consistency: Every generated prompt follows the same rigorous standards from next.md
