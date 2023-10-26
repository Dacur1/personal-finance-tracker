# Personal Finance Tracker Application Requirements
1. Introduction

    Project Name: Compaes
    Purpose: To develop a personal finance tracker that helps users manage their financial activities efficiently. Currently I am tracking my expenses and income using an excel sheet.
	Goal of this application is for me to be able to save expenses and income and visualize them customized for my own preference. Additionally any other future features can be extended and implemented due to it being my own application.

2. User Stories and Use Cases

        - User Registration
        - User Login
        - Adding Income
        - Adding Expenses
        - Viewing Financial Summaries
        - Setting Budgets
        - Generating Reports

3. Functional Requirements

        User Registration:
            - Users should be able to create an account with a unique username and password.
            - Users should receive a confirmation email for account activation.
        User Login:
            - Registered users should be able to log in securely.
			- Registered users should have the option to opt-in for a 2FA for better security.
        Adding Income:
            - Users should be able to add their income with a description, category, amount, date and source.
        Adding Expenses:
            - Users should be able to add expenses with descriptions, categories, payment methods, amount, date and source.
        Viewing Financial Summaries:
            - Users should be able to view their financial summaries, including income, expenses, and balances.
			- Users should be able to view visualizations to illustrate their financial situation for a better understanding.
        Setting Budgets:
            - Users should be able to set monthly or yearly budgets for different expense categories.
        Generating Reports:
            - Users should be able to generate reports, such as expense breakdowns, income vs. expenses, and budget vs. actual.
			- Users should be able to generate predicitive reports using statistical methods.

4. Non-Functional Requirements

        Performance: The application should load quickly and be able to be hosted on a Raspberry Pi and on Railway
        Security: User data should be stored securely, and user authentication should follow best practices.
        Scalability: The application should be scalable to accommodate future growth. The application should be extensible to provide additional features in the future.
        User Interface: The user interface should be user-friendly and responsive. Using an API the UI can then be easily adapted for different platforms.
        Accessibility: Optionally the application should be accessible to users with disabilities, since it is intended for personal use only
        Data Backup: Regular backups of user data should be performed, to prevent data loss due to server issues.

5. Technology Stack

	Front-end:
		- React.js
		- Material-UI library
	
	Back-end:
		- Java 
		- Spring Boot Framework (REST API)
		- Layer based architecture (Model, Service, Controller)
		- Hibernate
		
	Database:
		- PostgreSQL database

6. Data Model

	User:
		- ID
		- Email
		- Username
		- Password(hash)
		- Financial Account IDs
		
	Income:
		- ID
		- Description
		- Category
		- Amount
		- Date
		- Source
		
	Expense:
		- ID
		- Description
		- Category
		- Payment Method
		- Amount
		- Date
		- Source
		
	Source:
		- Name
	
	Financial Account:
		- ID
		- Name
		- Account Type
		- Balance
	
	Category:
		- Description
		
7. User Interface Design

    N/A

8. Testing Requirements

	Unit Testing:
        Definition: Unit testing focuses on verifying the correctness of individual components or functions in isolation.
        Approach: Write test cases for each function or method, covering various input scenarios, edge cases, and expected outcomes.

    Integration Testing:
        Definition: Integration testing checks how different components or modules work together as a group.
        Approach: Create test scenarios that involve interactions between multiple components. Ensure data flows correctly between them.

    User Acceptance Testing (UAT):
        Definition: UAT is conducted by end-users to validate that the software meets their business requirements.
        Approach: Collaborate with users to define test scenarios that mimic real-world usage. Users should confirm that the system functions as expected.
	
			
	User Registration:
		1. Successful Registration:
			- Input: Valid unique username, an usused email and a valid password 
			- Expected Outcome: User account is created, and a confirmation email is sent.

		2. Duplicate Username:
			- Input: Username that already exists
			- Expected Outcome: User receives an error message indicating that the username is already in use.
			
		3. Used Email:
			- Input: An already registered email
			- Expected Outcome: User receives an error message indicating that the email is already in use.

		4. Weak Password:
			- Input: A password that doesn't meet security requirements
			- Expected Outcome: User receives an error message about the password strength requirement.

		5. Email Confirmation:
			- Input: Successful registration
			- Expected Outcome: User receives a confirmation email with a link for account activation.

	User Login:
		1. Successful Login:
			- Input: Valid username and password
			- Expected Outcome: User is securely logged in.

		2. Incorrect Credentials:
			- Input: Invalid username or password
			- Expected Outcome: User receives an error message indicating incorrect credentials.

		3. Two-Factor Authentication (2FA):
			- Input: User chooses to enable 2FA
			- Expected Outcome: User is guided through the 2FA setup process, and 2FA is enabled for their account.

	Adding Income:
		1. Successful Income Addition:
			- Input: Valid income details (description, category, amount, date, source)
			- Expected Outcome: Income is added to the user's account.

		2. Missing Income Information:
			- Input: Incomplete income details
			- Expected Outcome: User receives an error message indicating missing information.

	Adding Expenses:
		1. Successful Expense Addition:
			- Input: Valid expense details (description, category, payment method, amount, date, source)
			- Expected Outcome: Expense is added to the user's account.

		2. Missing Expense Information:
			- Input: Incomplete expense details
			- Expected Outcome: User receives an error message indicating missing information.

	Setting Budgets:
		1. Setting Monthly Budget:
			- Input: User sets a monthly budget for a specific expense category
			- Expected Outcome: The monthly budget for that category is saved.

		2. Setting Yearly Budget:
			Input: User sets a yearly budget for a specific expense category
			Expected Outcome: The yearly budget for that category is saved.

		3. Invalid Budget Amount:
			- Input: User attempts to set a budget with a negative or zero amount
			- Expected Outcome: User receives an error message indicating that the budget amount is invalid.

9. Deployment

    Hosting Platforms:
		Web Server:
			- Railway
		
		Database Server:
			- PostgreSQL on a Docker container
		
		Frontend Hosting:
			- Vercel
		
		(Additionally the whole application should also be deployed via a private Raspberry Pi 4GB RAM)
	
	Deployment Pipeline
		Tool: Github Actions
		
		Version Control: Use Git for version control and host your repository on platforms like GitHub or GitLab.

		Continuous Integration (CI): Whenever code changes are pushed to the repository, the CI server (e.g., Jenkins) automatically builds and tests the application.

		Testing: In the CI environment, run unit tests and integration tests to ensure that code changes do not introduce regressions.

		Artifact Generation: After successful testing, create build artifacts (e.g., compiled code, Docker containers).
		
		Deployment to Production: After successfull artifact generation, automatically deploy to the production environment.
		
		Database Migrations: Automate database schema migrations to keep the database in sync with code changes.

		Monitoring and Rollback: In case of issues, have a rollback mechanism to revert to the previous stable version.

		Continuous Delivery (CD): For a mature pipeline, consider implementing continuous delivery, where changes automatically go to production after successful testing.		
