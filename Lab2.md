
![Phanttext](https://www.planttext.com/api/plantuml/png/Z9B1JiCm38RlUGeVkqDVO4BJO49STgWsNi2qMOb8d2fn4MFYoJZmIBm2IMZNgYiJjxh-_VctdU_FhxLdTDmQBKIfqNkuGthPCx8qajZV4khZktGWJW80a58qvBE3qh90VeObxDafgXTBUBMgYkfQygDbr8Mp1yLRwtss2BhAjazQzWA7vB5aPMbZM-BCM1hJmjUCwanlxjyQIJAGjJAAWreHnwAjydoJabwk1lac6A-jEoOZlot4Hp_wg4iQDw-2Uj257sXYz_4CUTaHppg0WTWP42T8EEbBfvh8lqgTCrIWy-aCaGHDZ6Pstmy-AboDxEnaOnq_X8KvPEiwMDt7-zOO3BjXXrtn72ysIHSEs3yUIvwlBhrV4q-D_OyhBlSpLKp0ATyVHQmbLU7b_m000F__0m00)

# Explanation of SRP, Cohesion, and Coupling

#Single Responsibility Principle (SRP):
Each class in the design has a single responsibility. For instance:
BankStatementAnalyzer: Responsible for analyzing bank statements and providing insights.
Transaction: Represents a single bank transaction.
Expense: Represents an expense with a description and amount.
TransactionParser: Responsible for parsing the CSV file and converting it into a list of Transaction objects.
ReportGenerator: Responsible for generating reports and summaries based on the list of transactions.
This separation ensures that changes in one class (e.g., how transactions are parsed) do not affect others.

# Cohesion:
The classes are designed to be cohesive, meaning that the methods and attributes within each class are closely related to the class's purpose.
For example, TransactionParser has methods that are solely related to parsing transactions, while ReportGenerator focuses on generating reports based on transactions.
High cohesion within classes improves maintainability and readability, as each class has a clear and focused role.

# Coupling:
The design aims for low coupling between classes, meaning that they are independent and changes in one class have minimal impact on others.
BankStatementAnalyzer interacts with TransactionParser and ReportGenerator, but these components can be modified or replaced without affecting the core functionality of the analyzer.
For example, if a different format of bank statements is introduced, only the TransactionParser class would need to change, while the analysis and reporting functionalities remain intact.
