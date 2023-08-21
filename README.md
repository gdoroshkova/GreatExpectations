What was done:
1. Install Great Expectations: 
pip install great-expectations

2. Initialize a New Project. Navigate to desired project directory and run:
great_expectations init

3. Set Up MS SQL Datasource. Edit the great_expectations.yml configuration file to include MS SQL datasource:
great_expectations datasource new
Following the prompts to configure the datasource.
Data source was added for the TRN database for testing 'employees' table.

4. Create Expectations Automatically using Profiler. Create an Expectation Suite:
great_expectations suite new
Follow the prompts, and select "Automatically, using a Data Assistant" when asked for the type of suite.
Profiler metrics were generated automatically.

5. Edit expectations:
great_expectations suite edit expec_employees
Test suits for 'employees' table was created.
Add Column Expectation(s):
expect_column_min_to_be_between(), 
expect_column_max_to_be_between(),
expect_column_mean_to_be_between(),
expect_column_values_to_be_unique(), 
expect_column_values_to_be_between(),
expect_column_values_to_not_be_null()

6. Generate Data Docs:
Build the Data Docs to explore the generated expectations and validation results:
great_expectations docs build
Results of executed are reported using data docs report

7. Create a Checkpoint:
great_expectations checkpoint new my_checkpoint

8. Change Data to Fail Checks
Modify Data:
INSERT INTO hr.employees (first_name, last_name, email, phone_number, hire_date, job_id, salary, manager_id, department_id)
VALUES ('Halina', 'Dar', '123@gmail.com', '7654328970', '2023-08-21', 19, 25000, 205, 11);

9. Run my_checkpoint checkpoint:
great_expectations checkpoint run my_checkpoint
Testing consolidated to checkpoint and executed from it.

10. Generate Data Docs:
Build the Data Docs to explore the generated expectations and validation results again:
great_expectations docs build