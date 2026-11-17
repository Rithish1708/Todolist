# Ex03 To-Do List using JavaScript
## Date:17-11-2026

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM

# index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Planify - Smart Task Planner</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <!-- Navigation -->
    <nav class="navbar">
        <h2>✦ Planify</h2>

        <div class="nav-links">
            <button class="nav active" data-filter="all">
                Dashboard
            </button>

            <button class="nav" data-filter="pending">
                Pending
            </button>

            <button class="nav" data-filter="completed">
                Completed
            </button>
        </div>

        <button id="themeBtn">🌙 Theme</button>
    </nav>

    <main class="container">

        <!-- Welcome -->
        <section class="welcome">
            <div>
                <p class="small-title">YOUR PERSONAL PLANNER</p>
                <h1>Make Today Count! ✨</h1>
                <p>Plan your work, manage your time and achieve more.</p>
            </div>

            <div class="welcome-icon">📅</div>
        </section>

        <!-- Statistics -->
        <section class="stats">

            <div class="stat-card purple">
                <span>📋 Total Tasks</span>
                <h2 id="totalTasks">0</h2>
                <p>All activities</p>
            </div>

            <div class="stat-card pink">
                <span>⏳ Pending</span>
                <h2 id="pendingTasks">0</h2>
                <p>Waiting to finish</p>
            </div>

            <div class="stat-card green">
                <span>✓ Completed</span>
                <h2 id="completedTasks">0</h2>
                <p>Successfully done</p>
            </div>

            <div class="stat-card orange">
                <span>📈 Progress</span>
                <h2 id="progress">0%</h2>
                <p>Your achievement</p>
            </div>

        </section>

        <!-- Productivity -->
        <section class="progress-card">
            <div class="progress-heading">
                <h3>🌟 Your Productivity</h3>
                <span id="progressText">0% completed</span>
            </div>

            <div class="progress-track">
                <div id="progressBar"></div>
            </div>
        </section>

        <!-- Create Task -->
        <section class="panel">

            <h2>✏️ Create a New Task</h2>
            <p class="description">Add your activities and stay organized.</p>

            <form id="taskForm">

                <input
                    type="text"
                    id="taskInput"
                    placeholder="What do you need to do?"
                    required
                >

                <select id="category">
                    <option value="Personal">Personal</option>
                    <option value="College">College</option>
                    <option value="Work">Work</option>
                    <option value="Other">Other</option>
                </select>

                <select id="priority">
                    <option value="Low">Low Priority</option>
                    <option value="Medium" selected>Medium Priority</option>
                    <option value="High">High Priority</option>
                </select>

                <input type="date" id="dueDate">

                <button type="submit" class="add-btn">
                    + Create Task
                </button>

            </form>

        </section>

        <!-- Task List -->
        <section class="panel">

            <div class="task-heading">
                <div>
                    <h2>My Activities 📝</h2>
                    <p class="description">Your daily tasks in one place.</p>
                </div>

                <button id="clearBtn" class="clear-btn">
                    Clear Completed
                </button>
            </div>

            <div class="tools">

                <input
                    type="search"
                    id="searchInput"
                    placeholder="🔍 Search your activities..."
                >

                <select id="categoryFilter">
                    <option value="all">All Categories</option>
                    <option value="Personal">Personal</option>
                    <option value="College">College</option>
                    <option value="Work">Work</option>
                    <option value="Other">Other</option>
                </select>

            </div>

            <div class="filter-buttons">

                <button class="filter active" data-filter="all">
                    All Tasks
                </button>

                <button class="filter" data-filter="pending">
                    Pending
                </button>

                <button class="filter" data-filter="completed">
                    Completed
                </button>

            </div>

            <div id="taskList"></div>

            <p id="emptyMessage" class="empty">
                🌸 No activities found. Start by adding a task!
            </p>

        </section>

        <footer>
            Made with ♥ by RITHISH R|
            Register Number:212224040278
        </footer>

    </main>

    <script src="script.js"></script>
</body>
</html>
```
# style.css
```
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Arial, sans-serif;
    background: #f8f6ff;
    color: #352d50;
    transition: 0.3s;
}

/* Navigation */

.navbar {
    background: white;
    padding: 20px 7%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: 0 3px 15px #5c45850d;
}

.navbar h2 {
    color: #7955c8;
    font-size: 26px;
}

.nav-links {
    display: flex;
    gap: 12px;
}

.nav {
    background: transparent;
    border: none;
    padding: 11px 17px;
    border-radius: 8px;
    color: #766c8c;
    cursor: pointer;
}

.nav.active,
.nav:hover {
    background: #eee7ff;
    color: #7955c8;
}

#themeBtn {
    background: #eee7ff;
    border: none;
    padding: 11px 16px;
    border-radius: 8px;
    color: #7955c8;
    cursor: pointer;
}

/* Main Container */

.container {
    max-width: 1150px;
    margin: 35px auto;
    padding: 0 25px;
}

/* Welcome Section */

.welcome {
    background: linear-gradient(120deg, #7653c9, #b18be9);
    color: white;
    padding: 35px;
    border-radius: 18px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 25px;
}

.small-title {
    font-size: 12px;
    letter-spacing: 2px;
    margin-bottom: 12px;
    opacity: 0.8;
}

.welcome h1 {
    font-size: 32px;
    margin-bottom: 10px;
}

.welcome p {
    font-size: 14px;
}

.welcome-icon {
    font-size: 65px;
    background: #ffffff25;
    padding: 15px;
    border-radius: 20px;
}

/* Statistics */

.stats {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 18px;
    margin-bottom: 22px;
}

.stat-card {
    padding: 23px;
    border-radius: 14px;
    background: white;
    border: 1px solid #eee9f7;
    box-shadow: 0 4px 15px #4d39720a;
}

.stat-card span {
    font-size: 14px;
    color: #756d88;
}

.stat-card h2 {
    font-size: 31px;
    margin: 13px 0 5px;
}

.stat-card p {
    color: #9992a9;
    font-size: 12px;
}

.purple h2 { color: #7955c8; }
.pink h2 { color: #e56b9c; }
.green h2 { color: #36a982; }
.orange h2 { color: #e69a4a; }

/* Progress */

.progress-card,
.panel {
    background: white;
    padding: 26px;
    border-radius: 15px;
    margin-bottom: 22px;
    border: 1px solid #eee9f7;
    box-shadow: 0 4px 15px #4d39720a;
}

.progress-heading {
    display: flex;
    justify-content: space-between;
    margin-bottom: 17px;
    gap: 10px;
}

.progress-heading span {
    color: #7955c8;
    font-size: 13px;
}

.progress-track {
    height: 11px;
    background: #eee9f7;
    border-radius: 20px;
    overflow: hidden;
}

#progressBar {
    height: 100%;
    width: 0%;
    background: linear-gradient(90deg, #8c65d8, #e68bb6);
    border-radius: 20px;
    transition: 0.4s;
}

/* Create Task */

.panel h2 {
    font-size: 20px;
    margin-bottom: 7px;
}

.description {
    color: #9992a9;
    font-size: 13px;
    margin-bottom: 20px;
}

form {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr auto;
    gap: 10px;
}

input,
select {
    padding: 12px;
    border: 1px solid #e5dff0;
    border-radius: 8px;
    outline: none;
    background: #fdfcff;
    color: #453b5d;
    min-width: 0;
}

input:focus,
select:focus {
    border-color: #9b79dc;
}

button {
    cursor: pointer;
}

.add-btn {
    background: #7955c8;
    color: white;
    border: none;
    padding: 12px 17px;
    border-radius: 8px;
}

.add-btn:hover {
    background: #6040a6;
}

/* Task Section */

.task-heading {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 12px;
}

.clear-btn {
    background: #fff0f4;
    color: #d95c88;
    border: none;
    padding: 11px 15px;
    border-radius: 8px;
}

.tools {
    display: flex;
    gap: 12px;
    margin-bottom: 18px;
}

.tools input {
    flex: 1;
}

.filter-buttons {
    display: flex;
    gap: 9px;
    margin-bottom: 18px;
}

.filter {
    padding: 10px 18px;
    border: none;
    border-radius: 8px;
    background: #f0ebfa;
    color: #776b91;
}

.filter.active,
.filter:hover {
    background: #7955c8;
    color: white;
}

/* Task Cards */

.task-card {
    display: flex;
    align-items: center;
    gap: 13px;
    padding: 17px;
    margin-bottom: 12px;
    border-radius: 11px;
    background: #fcfaff;
    border: 1px solid #eee8f8;
}

.task-card input[type="checkbox"] {
    width: 18px;
    height: 18px;
    accent-color: #7955c8;
}

.task-info {
    flex: 1;
    min-width: 0;
}

.task-info h3 {
    font-size: 15px;
    overflow-wrap: anywhere;
}

.task-info h3.done {
    text-decoration: line-through;
    color: #aaa3b7;
}

.task-info p {
    font-size: 12px;
    color: #a19aad;
    margin-top: 7px;
}

.tag {
    font-size: 11px;
    padding: 6px 11px;
    border-radius: 20px;
    white-space: nowrap;
}

.High {
    background: #ffe4e9;
    color: #d94c69;
}

.Medium {
    background: #fff0dc;
    color: #c17b27;
}

.Low {
    background: #e0f6e9;
    color: #319568;
}

.actions {
    display: flex;
    gap: 7px;
}

.actions button {
    border: none;
    padding: 8px 12px;
    border-radius: 7px;
}

.edit-btn {
    background: #eee7ff;
    color: #7955c8;
}

.delete-btn {
    background: #ffe8ed;
    color: #d94c69;
}

.empty {
    display: none;
    text-align: center;
    padding: 30px;
    color: #a19aad;
}

/* Footer */

footer {
    text-align: center;
    padding: 25px 10px;
    color: #9992a9;
    font-size: 13px;
}

/* Dark Mode */

body.dark {
    background: #1c1930;
    color: #f5efff;
}

body.dark .navbar,
body.dark .stat-card,
body.dark .panel,
body.dark .progress-card {
    background: #29243e;
    border-color: #403957;
}

body.dark .navbar h2,
body.dark .panel h2,
body.dark .progress-heading h3 {
    color: #eee5ff;
}

body.dark .task-card {
    background: #332d49;
    border-color: #49405e;
}

body.dark .task-info h3 {
    color: white;
}

body.dark .task-info h3.done {
    color: #aaa3b7;
}

body.dark input,
body.dark select {
    background: #332d49;
    color: white;
    border-color: #49405e;
}

body.dark .nav,
body.dark .filter {
    color: #ddd0f6;
}

body.dark .nav.active,
body.dark .filter.active {
    background: #7955c8;
    color: white;
}

body.dark .progress-track {
    background: #49405e;
}

/* Responsive Design */

@media (max-width: 950px) {
    form {
        grid-template-columns: 1fr 1fr;
    }

    .stats {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (max-width: 650px) {
    .navbar {
        flex-wrap: wrap;
        gap: 15px;
        padding: 16px;
    }

    .nav-links {
        order: 3;
        width: 100%;
        flex-wrap: wrap;
    }

    .container {
        padding: 0 14px;
        margin-top: 20px;
    }

    .welcome {
        padding: 23px;
    }

    .welcome h1 {
        font-size: 23px;
    }

    .welcome-icon {
        font-size: 35px;
    }

    .stats {
        gap: 10px;
    }

    .stat-card {
        padding: 15px;
    }

    form {
        grid-template-columns: 1fr;
    }

    .tools {
        flex-direction: column;
    }

    .task-heading {
        align-items: flex-start;
        flex-direction: column;
    }

    .task-card {
        flex-wrap: wrap;
    }

    .actions {
        margin-left: auto;
    }

    .filter-buttons {
        flex-wrap: wrap;
    }
}
```
# script.js
```
// Get HTML elements
const taskForm = document.getElementById("taskForm");
const taskInput = document.getElementById("taskInput");
const category = document.getElementById("category");
const priority = document.getElementById("priority");
const dueDate = document.getElementById("dueDate");
const taskList = document.getElementById("taskList");
const searchInput = document.getElementById("searchInput");
const categoryFilter = document.getElementById("categoryFilter");

let tasks = JSON.parse(localStorage.getItem("myTasks")) || [];
let currentFilter = "all";

// Save tasks in Local Storage
function saveTasks() {
    localStorage.setItem("myTasks", JSON.stringify(tasks));
}

// Add new task
taskForm.addEventListener("submit", function(e) {
    e.preventDefault();

    const name = taskInput.value.trim();

    if (name === "") {
        alert("Please enter a task!");
        return;
    }

    const task = {
        id: Date.now(),
        name: name,
        category: category.value,
        priority: priority.value,
        dueDate: dueDate.value,
        completed: false
    };

    tasks.push(task);

    saveTasks();
    taskForm.reset();

    priority.value = "Medium";
    displayTasks();
});

// Display tasks
function displayTasks() {

    taskList.innerHTML = "";

    let search = searchInput.value.toLowerCase();
    let selectedCategory = categoryFilter.value;

    let filteredTasks = tasks.filter(function(task) {

        let matchSearch = task.name.toLowerCase()
            .includes(search);

        let matchCategory =
            selectedCategory === "all" ||
            task.category === selectedCategory;

        let matchStatus =
            currentFilter === "all" ||
            (currentFilter === "pending" && !task.completed) ||
            (currentFilter === "completed" && task.completed);

        return matchSearch && matchCategory && matchStatus;
    });

    filteredTasks.forEach(function(task) {

        let card = document.createElement("div");
        card.className = "task-card";

        // Checkbox
        let checkbox = document.createElement("input");
        checkbox.type = "checkbox";
        checkbox.checked = task.completed;

        checkbox.addEventListener("change", function() {
            toggleTask(task.id);
        });

        // Task information
        let info = document.createElement("div");
        info.className = "task-info";

        let title = document.createElement("h3");
        title.textContent = task.name;

        if (task.completed) {
            title.classList.add("done");
        }

        let details = document.createElement("p");

        let dateText = task.dueDate
            ? " | Due: " + task.dueDate
            : " | No deadline";

        details.textContent =
            task.category + dateText;

        info.append(title, details);

        // Priority label
        let tag = document.createElement("span");
        tag.className = "tag " + task.priority;
        tag.textContent = task.priority;

        // Edit button
        let editBtn = document.createElement("button");
        editBtn.className = "edit-btn";
        editBtn.textContent = "Edit";

        editBtn.addEventListener("click", function() {
            editTask(task.id);
        });

        // Delete button
        let deleteBtn = document.createElement("button");
        deleteBtn.className = "delete-btn";
        deleteBtn.textContent = "Delete";

        deleteBtn.addEventListener("click", function() {
            deleteTask(task.id);
        });

        let actions = document.createElement("div");
        actions.className = "actions";
        actions.append(editBtn, deleteBtn);

        card.append(checkbox, info, tag, actions);

        taskList.appendChild(card);
    });

    // Empty message
    document.getElementById("emptyMessage").style.display =
        filteredTasks.length === 0 ? "block" : "none";

    updateStatistics();
}

// Complete or uncomplete task
function toggleTask(id) {

    tasks = tasks.map(function(task) {
        if (task.id === id) {
            task.completed = !task.completed;
        }
        return task;
    });

    saveTasks();
    displayTasks();
}

// Edit task
function editTask(id) {

    let task = tasks.find(t => t.id === id);

    let newName = prompt("Enter updated task name:", task.name);

    if (newName !== null && newName.trim() !== "") {

        task.name = newName.trim();

        saveTasks();
        displayTasks();
    }
}

// Delete task
function deleteTask(id) {

    if (confirm("Are you sure you want to delete this task?")) {

        tasks = tasks.filter(t => t.id !== id);

        saveTasks();
        displayTasks();
    }
}

// Filter tasks
function setFilter(value) {

    currentFilter = value;

    document.querySelectorAll(".filter, .nav")
        .forEach(function(button) {

            button.classList.toggle(
                "active",
                button.dataset.filter === value
            );
        });

    displayTasks();
}

// Filter button events
document.querySelectorAll(".filter, .nav")
    .forEach(function(button) {

        button.addEventListener("click", function() {
            setFilter(button.dataset.filter);
        });
    });

// Search tasks
searchInput.addEventListener("input", displayTasks);

// Category filter
categoryFilter.addEventListener("change", displayTasks);

// Clear completed tasks
document.getElementById("clearBtn")
    .addEventListener("click", function() {

        if (confirm("Delete all completed tasks?")) {

            tasks = tasks.filter(t => !t.completed);

            saveTasks();
            displayTasks();
        }
    });

// Update dashboard statistics
function updateStatistics() {

    let total = tasks.length;

    let completed = tasks.filter(
        t => t.completed
    ).length;

    let pending = total - completed;

    let percentage = total === 0
        ? 0
        : Math.round((completed / total) * 100);

    document.getElementById("totalTasks")
        .textContent = total;

    document.getElementById("pendingTasks")
        .textContent = pending;

    document.getElementById("completedTasks")
        .textContent = completed;

    document.getElementById("progress")
        .textContent = percentage + "%";

    document.getElementById("progressText")
        .textContent = percentage + "% completed";

    document.getElementById("progressBar")
        .style.width = percentage + "%";
}

// Dark and light mode
const themeBtn = document.getElementById("themeBtn");

if (localStorage.getItem("theme") === "dark") {
    document.body.classList.add("dark");
}

function updateThemeButton() {
    themeBtn.textContent = document.body.classList.contains("dark")
        ? "☀️ Light Mode"
        : "🌙 Dark Mode";
}

updateThemeButton();

themeBtn.addEventListener("click", function() {

    document.body.classList.toggle("dark");

    let theme = document.body.classList.contains("dark")
        ? "dark"
        : "light";

    localStorage.setItem("theme", theme);

    updateThemeButton();
});

// Initial display
displayTasks();
```


## OUTPUT

![alt text](<Screenshot (171).png>)

## RESULT
The program for creating To-do list using JavaScript is executed successfully.
