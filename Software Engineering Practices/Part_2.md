# Testing

Testing your code is essential before deployment, as it helps catch errors and ensures the quality of your analysis. Proper testing avoids unexpected issues and builds confidence in your results, which is crucial in data science where problems may not always be easily detectable.

## Test-Driven Development (TDD)
Test-driven development is a process where you write tests for tasks before implementing the code. This approach ensures that your code meets the requirements and helps catch errors early in the development cycle.

## Unit Tests
Unit tests cover individual units of code, such as a single function, and are designed to be repeatable and automated. They isolate code from external dependencies, making it easier to identify issues in specific parts of the program. However, they are not sufficient alone, as integration tests are needed to ensure all components work together.

## Unit Testing Tools
To use unit testing tools like pytest, install it with `pip install -U pytest`. Create test files starting with `test_`, define test functions within these files, and run `pytest` in your terminal to execute the tests. In the test output, periods indicate successful tests and Fs indicate failures. It is recommended to have only one assert statement per test for clarity in identifying issues.

# Test-Driven Development and Logging

## Test-Driven Development (TDD) and Data Science
Test-driven development involves writing tests before implementing the corresponding code. Initially, the tests will fail, and you complete a task when the tests pass successfully. This approach allows you to check for various scenarios and edge cases before coding, providing immediate feedback on your function’s correctness. In data science, TDD is gaining traction as a way to ensure that code remains reliable and maintainable, especially during refactoring or updates. It helps confirm that your function behaves consistently across different environments and conditions.

## Logging
Logging is crucial for understanding the events and behaviors of your program during execution. Effective logging helps diagnose issues by providing context for unexpected results or failures. For instance, if your model produces unexpected outcomes after running overnight, log messages can offer insights into the circumstances that led to those results. Good logging practices enable you to track and analyze the program's performance and behavior, making it easier to troubleshoot and improve your code.

## Log Messages

Logging involves recording messages to document events that occur during software execution. Here are some tips for writing effective log messages:

### Tip 1: Be Professional and Clear
Avoid ambiguous language in your logs. Instead of using casual or unclear terms like "Hmmm... this isn't working???" or "idk.... :(", be precise and professional. For example: "Couldn't parse file."

### Tip 2: Be Concise and Use Normal Capitalization
Keep your log messages brief and to the point, and use standard capitalization. Rather than verbose messages like "We have completed the steps necessary and will now proceed with the recommendation process for the records in our product database," use concise wording such as "Generating product recommendations."

### Tip 3: Choose the Appropriate Level for Logging
Select the right logging level based on the situation:
- **Debug**: For detailed messages about the program's operations.
- **Error**: For recording errors that occur during execution.
- **Info**: For logging actions that are user-driven or system-specific, such as scheduled operations.

### Tip 4: Provide Useful Information
Ensure your log messages include pertinent details. Instead of a vague message like "Failed to read location data," provide additional context: "Failed to read location data: store_id 8324971."

## Tips for Conducting a Code Review

### Tip 1: Use a Code Linter
While not directly part of the code review process, using a code linter like pylint can significantly streamline reviews by automatically checking for coding standards and PEP 8 guidelines. It's also beneficial to agree on a team style guide, which can address any style disagreements and ensure consistency across the codebase.

### Tip 2: Explain Issues and Make Suggestions
Rather than directing changes authoritatively, explain the impact of the current code and suggest improvements. This approach fosters a constructive dialogue and acknowledges that there may be intentional design choices. For instance, instead of saying, "Make model evaluation code its own module - too repetitive," you could say, "How about we consider making the model evaluation code its own module? This would simplify `models.py` and allow us to reuse evaluation methods with different models."

### Tip 3: Keep Your Comments Objective
Avoid personal language in comments to maintain a focus on the code itself rather than on individuals. For example, rather than saying, "I wouldn't groupby genre twice like you did here," use, "Can we group by genre at the beginning of the function and then use that groupby object to get the average prices and views without repeating the computation?"

### Tip 4: Provide Code Examples
To make your feedback actionable and save time, provide code examples with your suggestions. For example, instead of stating, "You can do this all in one step by using the pandas str.split method," you could show the exact code change: "We can simplify this step using the pandas str.split method as shown below. Found this solution here: https://stackoverflow.com/questions/14745022/how-to-split-a-column-into-two-columns
```python
df['first_name'], df['last_name'] = df['name'].str.split(' ', 1).str
```"

