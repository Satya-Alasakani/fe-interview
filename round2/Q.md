1️⃣ CSS Task

	Q1) Create a pricing card layout with 3 plans in a row.
		VQA Feedback:
		Highlight the “Recommended” plan with a badge.

	Q2) Build a Kanban Board layout with columns for “To Do”, “In Progress”, “Done”.
		VQA Feedback:
		Apply color-coded headers for each column.


2️⃣ Framework Task

	Q1) Create a File Manager page:
		Sidebar → Folder tree
		Main → Grid view of files with checkbox selection & toolbar actions
		
		Ask: Component breakdown + API endpoints (list, upload, delete).


	Q2) Implement Order History page:
		Sidebar → Filters (Date, Status)
		Main → Paginated list of orders
		Ask: Component structure + APIs
		Expected → GET /orders?status=&dateRange=


3️⃣ Data Structure for State Management

Q1) Problem: Privilege management page
You are building a Privilege Settings Page for a product.
	A Privilege can be:
	Standalone – Can be selected/unselected independently.
	Dependent – Has child privileges that should automatically reflect the parent’s state.
	Requirements:

		Selecting a parent privilege → Automatically selects all dependent privileges.
		Unselecting a parent privilege → Automatically unselects all dependent privileges.
		If all child privileges are unchecked manually → The parent should auto-uncheck.
		If any child privilege is checked manually → The parent should auto-check (optional) depending on UX rules.
		Maintain a consistent state object for privileges.

	const privileges = [
	  { id: 'view', label: 'View Dashboard', dependencies: [] },
	  { id: 'edit', label: 'Edit Dashboard', dependencies: ['view'] },
	  { id: 'delete', label: 'Delete Dashboard', dependencies: ['edit'] },
	  { id: 'export', label: 'Export Data', dependencies: ['view'] },
	];



	Here:

		View is standalone.
		Edit depends on View.
		Delete depends on Edit → (transitive dependency on View).
		Export depends on View.


Q1) Problem: Efficient Client-Side Logger with Batching

	Scenario
		You are building a client-side logger for a web application:

		The logger collects logs like errors, warnings, and performance events.
		Logs arrive frequently (hundreds per second).
		Each log must be sent to the server to be saved.
		Sending a request per log will flood the server with API calls.


	Implement a Logger class with methods: log(message)
	
	Use efficient data structures and techniques to:
	Collect logs in memory
	Batch them and send asynchronously
	Minimize network requests





