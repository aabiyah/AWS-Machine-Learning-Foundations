# Clean and Modular Code

## Key Concepts

### Production Code
- **Definition**: Software running on production servers to handle live users and data of the intended audience.
- **Note**: This is different from production-quality code, which describes code that meets expectations for production in reliability, efficiency, and other aspects. Ideally, all code in production meets these expectations, but this is not always the case.

### Clean Code
- **Definition**: Code that is readable, simple, and concise.
- **Importance**: Clean production-quality code is crucial for collaboration and maintainability in software development.

### Modular Code
- **Definition**: Code that is logically broken up into functions and modules.
- **Benefits**: Modular production-quality code makes your code more organized, efficient, and reusable.

### Module
- **Definition**: A file. Modules allow code to be reused by encapsulating them into files that can be imported into other files.

## Refactoring Code

### Refactoring
- **Definition**: Restructuring your code to improve its internal structure without changing its external functionality. This gives you a chance to clean and modularize your program after you've got it working.
- **Purpose**: Since it isn't easy to write your best code while you're still trying to just get it working, allocating time to do this is essential to producing high-quality code.
- **Benefits**: Despite the initial time and effort required, refactoring really pays off by speeding up your development time in the long run.

### Importance of Refactoring
- You become a much stronger programmer when you're constantly looking to improve your code.
- The more you refactor, the easier it will be to structure and write good code the first time.


## Writing Clean Code: Meaningful Names

Use Meaningful Names

- **Be descriptive and imply type**: 
  - For booleans, you can prefix with `is_` or `has_` to make it clear it is a condition.
  - Use parts of speech to imply types, like using verbs for functions and nouns for variables.
  
- **Be consistent but clearly differentiate**: 
  - `age_list` and `age` are easier to differentiate than `ages` and `age`.
  
- **Avoid abbreviations and single letters**: 
  - Determine when to make these exceptions based on the audience for your code.
  - If you work with other data scientists, certain variables may be common knowledge.
  - If you work with full-stack engineers, it might be necessary to provide more descriptive names in these cases as well.
  - Exceptions include counters and common math variables.
  
- **Long names aren't the same as descriptive names**: 
  - Be descriptive, but only with relevant information.
  - Good function names describe what they do well without including details about implementation or highly specific uses.
  
- **Test the effectiveness of your names**: 
  - Ask a fellow programmer to guess the purpose of a function or variable based on its name, without looking at your code.
  - Coming up with meaningful names often requires effort to get right.

## Writing Clean Code: Nice Whitespace

Use Whitespace Properly

- **Organize your code with consistent indentation**: 
  - The standard is to use four spaces for each indent.
  - Set this as a default in your text editor.
  
- **Separate sections with blank lines**: 
  - Keep your code well organized and readable.
  
- **Limit your lines to around 79 characters**: 
  - This is the guideline given in the PEP 8 style guide.
  - Many good text editors have a setting to display a subtle line that indicates where the 79 character limit is.
 
## Writing Modular Code

Follow the tips below to write modular code.

### Tip 1: DRY (Don't Repeat Yourself)
Don't repeat yourself! Modularization allows you to reuse parts of your code. Generalize and consolidate repeated code in functions or loops.

### Tip 2: Abstract Out Logic to Improve Readability
Abstracting out code into a function not only makes it less repetitive but also improves readability with descriptive function names. Although your code can become more readable when you abstract out logic into functions, it is possible to over-engineer this and have way too many modules, so use your judgment.

### Tip 3: Minimize the Number of Entities (Functions, Classes, Modules, etc.)
There are trade-offs to having function calls instead of inline logic. If you have broken up your code into an unnecessary amount of functions and modules, you'll have to jump around everywhere if you want to view the implementation details for something that may be too small to be worth it. Creating more modules doesn't necessarily result in effective modularization.

### Tip 4: Functions Should Do One Thing
Each function you write should be focused on doing one thing. If a function is doing multiple things, it becomes more difficult to generalize and reuse. Generally, if there's an "and" in your function name, consider refactoring.

### Tip 5: Arbitrary Variable Names Can Be More Effective in Certain Functions
Arbitrary variable names in general functions can actually make the code more readable.

### Tip 6: Try to Use Fewer Than Three Arguments Per Function
Try to use no more than three arguments when possible. This is not a hard rule and there are times when it is more appropriate to use many parameters. But in many cases, it's more effective to use fewer arguments. Remember we are modularizing to simplify our code and make it more efficient. If your function has a lot of parameters, you may want to rethink how you are splitting this up.

## Efficient Code

Knowing how to write code that runs efficiently is another essential skill in software development. Optimizing code to be more efficient can mean making it:

- **Execute faster**
- **Take up less space in memory/storage**

The project on which you're working determines which of these is more important to optimize for your company or product. When you're performing lots of different transformations on large amounts of data, this can make orders of magnitude of difference in performance.

## Documentation

**Documentation**: Additional text or illustrated information that comes with or is embedded in the code of software.
Documentation is helpful for clarifying complex parts of code, making your code easier to navigate, and quickly conveying how and why different components of your program are used.

Several types of documentation can be added at different levels of your program:

- **Inline comments** - line level
- **Docstrings** - module and function level
- **Project documentation** - project level

## Inline Comments

**Inline comments** are text following hash symbols (`#`) throughout your code. They are used to explain parts of your code and help future contributors understand your work.

- **Purpose**: 
  - Document the major steps of complex code.
  - Explain the history or rationale behind specific implementations.
  - Clarify unconventional or seemingly arbitrary approaches due to external variables or side effects.

- **Best Practices**:
  - Use comments to supplement and clarify the code, not to justify bad code.
  - If code requires extensive comments to be understood, consider refactoring the code to make it more readable.

# Docstrings

**Docstrings**, or documentation strings, are valuable pieces of documentation that explain the functionality of any function or module in your code. Ideally, each of your functions should always have a docstring.

- **Format**: 
  - Docstrings are surrounded by triple quotes (`"""` or `'''`).
  - The first line of the docstring is a brief explanation of the function's purpose.

### One-line docstring

def population_density(population, land_area):
    """Calculate the population density of an area."""
    return population / land_area

### Multi-line docstring
If the function is complicated enough to warrant a longer description, you can add a more thorough paragraph after the one-line summary.

def population_density(population, land_area):
    """Calculate the population density of an area.

    Args:
        population (int): The population of the area.
        land_area (int or float): This function is unit-agnostic. If you pass in values in terms of square km or square miles, the function will return a density in those units.

    Returns:
        float: The population density of a particular area.
    """
    return population / land_area

### Elements of a Docstring
1. Summary: A brief explanation of the function's purpose.
2. Arguments:
- List the arguments.
- State their purpose.
- State the types of the arguments.
3. Returns: Provide a description of the output of the function.

Every piece of the docstring is optional; however, docstrings are a part of good coding practice and greatly aid in code readability and maintainability.

## Version Control in Data Science

### Git Branches
Git branches allow for isolated development, enabling you to work on new features or fixes without affecting the main codebase. This isolation facilitates parallel development, experimentation, and maintaining a clear history of changes.

### Git Log
The `git log` command provides a comprehensive history of commits, helping track changes, debug issues, and understand the project's evolution. It also assists in reverting to previous states if necessary.

### Commit Versions
Commit versions act as snapshots of your project at various points, offering a stable reference to roll back changes or track progress. They create a historical record that is crucial for collaboration and understanding code changes.

### Merging
Merging integrates changes from different branches, ensuring that work from multiple contributors is combined smoothly. It also helps maintain consistency in the codebase by resolving conflicts and keeping branches aligned with the main development line.


