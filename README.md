# Ex03 To-Do List using JavaScript
## Date: 23/2/2026
## Submitted by: Suchitra Nath (212223220112)

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
index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <div class="todo-app">
            <h1>My To-Do List</h1>
            
            <div class="input-container">
                <input 
                    type="text" 
                    id="taskInput" 
                    class="task-input" 
                    placeholder="Add a new task..."
                    autocomplete="off"
                >
                <button id="addBtn" class="add-btn">Add</button>
            </div>

            <div class="filter-buttons">
                <button class="filter-btn active" data-filter="all">All</button>
                <button class="filter-btn" data-filter="active">Active</button>
                <button class="filter-btn" data-filter="completed">Completed</button>
            </div>

            <ul id="taskList" class="task-list"></ul>

            <div class="task-stats">
                <span id="taskCount" class="stat">0 tasks</span>
                <button id="clearBtn" class="clear-btn">Clear Completed</button>
            </div>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>


```
style.css
```
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
}

.container {
    width: 100%;
    max-width: 600px;
}

.todo-app {
    background: white;
    border-radius: 15px;
    box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
    padding: 30px;
}

h1 {
    text-align: center;
    color: #333;
    margin-bottom: 30px;
    font-size: 2.5em;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

.input-container {
    display: flex;
    gap: 10px;
    margin-bottom: 20px;
}

.task-input {
    flex: 1;
    padding: 12px 16px;
    border: 2px solid #e0e0e0;
    border-radius: 8px;
    font-size: 16px;
    transition: border-color 0.3s;
}

.task-input:focus {
    outline: none;
    border-color: #667eea;
}

.add-btn {
    padding: 12px 30px;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    border: none;
    border-radius: 8px;
    font-size: 16px;
    font-weight: 600;
    cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s;
}

.add-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
}

.add-btn:active {
    transform: translateY(0);
}

.filter-buttons {
    display: flex;
    gap: 10px;
    margin-bottom: 20px;
    justify-content: center;
}

.filter-btn {
    padding: 8px 16px;
    border: 2px solid #e0e0e0;
    background: white;
    color: #666;
    border-radius: 8px;
    cursor: pointer;
    font-size: 14px;
    font-weight: 500;
    transition: all 0.3s;
}

.filter-btn:hover {
    border-color: #667eea;
    color: #667eea;
}

.filter-btn.active {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    border-color: transparent;
}

.task-list {
    list-style: none;
    margin-bottom: 20px;
    max-height: 400px;
    overflow-y: auto;
}

.task-item {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 12px;
    background: #f5f5f5;
    border-radius: 8px;
    margin-bottom: 8px;
    transition: all 0.3s;
}

.task-item:hover {
    background: #efefef;
    transform: translateX(5px);
}

.task-item.completed {
    opacity: 0.6;
}

.task-item.completed .task-text {
    text-decoration: line-through;
    color: #999;
}

.checkbox {
    width: 20px;
    height: 20px;
    cursor: pointer;
    accent-color: #667eea;
}

.task-text {
    flex: 1;
    color: #333;
    font-size: 15px;
    word-break: break-word;
}

.delete-btn {
    background: #ff6b6b;
    color: white;
    border: none;
    padding: 6px 12px;
    border-radius: 6px;
    cursor: pointer;
    font-size: 13px;
    transition: background 0.3s;
}

.delete-btn:hover {
    background: #ff5252;
}

.task-stats {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px;
    background: #f9f9f9;
    border-radius: 8px;
    font-size: 14px;
}

.stat {
    color: #666;
    font-weight: 500;
}

.clear-btn {
    background: #ffa500;
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 6px;
    cursor: pointer;
    font-size: 13px;
    transition: background 0.3s;
}

.clear-btn:hover {
    background: #ff9500;
}

.empty-state {
    text-align: center;
    padding: 40px 20px;
    color: #999;
}

.empty-state-icon {
    font-size: 50px;
    margin-bottom: 10px;
}

/* Scrollbar styling */
.task-list::-webkit-scrollbar {
    width: 8px;
}

.task-list::-webkit-scrollbar-track {
    background: #f1f1f1;
    border-radius: 10px;
}

.task-list::-webkit-scrollbar-thumb {
    background: #667eea;
    border-radius: 10px;
}

.task-list::-webkit-scrollbar-thumb:hover {
    background: #764ba2;
}

@media (max-width: 600px) {
    .todo-app {
        padding: 20px;
    }

    h1 {
        font-size: 2em;
        margin-bottom: 20px;
    }

    .filter-buttons {
        flex-wrap: wrap;
    }

    .task-item {
        flex-wrap: wrap;
    }
}

```
script.js
```
const taskInput = document.getElementById('taskInput');
const addBtn = document.getElementById('addBtn');
const taskList = document.getElementById('taskList');
const taskCount = document.getElementById('taskCount');
const clearBtn = document.getElementById('clearBtn');
const filterBtns = document.querySelectorAll('.filter-btn');

let tasks = [];
let currentFilter = 'all';

document.addEventListener('DOMContentLoaded', () => {
    loadTasks();
    renderTasks();
    setupEventListeners();
});

function setupEventListeners() {
    addBtn.addEventListener('click', addTask);
    taskInput.addEventListener('keypress', (e) => {
        if (e.key === 'Enter') addTask();
    });
    clearBtn.addEventListener('click', clearCompleted);
    filterBtns.forEach(btn => {
        btn.addEventListener('click', (e) => {
            filterBtns.forEach(b => b.classList.remove('active'));
            e.target.classList.add('active');
            currentFilter = e.target.dataset.filter;
            renderTasks();
        });
    });
}

function addTask() {
    const taskText = taskInput.value.trim();

    if (taskText === '') {
        alert('Please enter a task!');
        return;
    }

    const task = {
        id: Date.now(),
        text: taskText,
        completed: false,
        createdAt: new Date()
    };

    tasks.push(task);
    saveTasks();
    renderTasks();
    taskInput.value = '';
    taskInput.focus();
}

function toggleTask(id) {
    const task = tasks.find(t => t.id === id);
    if (task) {
        task.completed = !task.completed;
        saveTasks();
        renderTasks();
    }
}

function deleteTask(id) {
    tasks = tasks.filter(t => t.id !== id);
    saveTasks();
    renderTasks();
}

function clearCompleted() {
    const completedCount = tasks.filter(t => t.completed).length;
    
    if (completedCount === 0) {
        alert('No completed tasks to clear!');
        return;
    }

    if (confirm(`Clear ${completedCount} completed task(s)?`)) {
        tasks = tasks.filter(t => !t.completed);
        saveTasks();
        renderTasks();
    }
}

function renderTasks() {
    taskList.innerHTML = '';

    let filteredTasks = tasks;

    if (currentFilter === 'active') {
        filteredTasks = tasks.filter(t => !t.completed);
    } else if (currentFilter === 'completed') {
        filteredTasks = tasks.filter(t => t.completed);
    }

    if (filteredTasks.length === 0) {
        taskList.innerHTML = `
            <div class="empty-state">
                <div class="empty-state-icon">📝</div>
                <p>${currentFilter === 'all' ? 'No tasks yet. Add one to get started!' : 'No tasks found.'}</p>
            </div>
        `;
        updateTaskCount();
        return;
    }

    filteredTasks.forEach(task => {
        const li = document.createElement('li');
        li.className = `task-item ${task.completed ? 'completed' : ''}`;
        li.innerHTML = `
            <input 
                type="checkbox" 
                class="checkbox" 
                ${task.completed ? 'checked' : ''}
                onchange="toggleTask(${task.id})"
            >
            <span class="task-text">${escapeHtml(task.text)}</span>
            <button class="delete-btn" onclick="deleteTask(${task.id})">Delete</button>
        `;
        taskList.appendChild(li);
    });

    updateTaskCount();
}

function updateTaskCount() {
    const activeTasks = tasks.filter(t => !t.completed).length;
    const totalTasks = tasks.length;
    
    if (totalTasks === 0) {
        taskCount.textContent = '0 tasks';
    } else if (activeTasks === 0) {
        taskCount.textContent = `All done! (${totalTasks} task${totalTasks > 1 ? 's' : ''})`;
    } else {
        taskCount.textContent = `${activeTasks} of ${totalTasks} task${totalTasks > 1 ? 's' : ''} remaining`;
    }
}

function saveTasks() {
    localStorage.setItem('tasks', JSON.stringify(tasks));
}

function loadTasks() {
    const savedTasks = localStorage.getItem('tasks');
    if (savedTasks) {
        try {
            tasks = JSON.parse(savedTasks);
        } catch (e) {
            console.error('Error loading tasks:', e);
            tasks = [];
        }
    }
}

function escapeHtml(text) {
    const div = document.createElement('div');
    div.textContent = text;
    return div.innerHTML;
}

```
## OUTPUT
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4bf40f79-180d-4cd5-af46-e243eda3c3e1" />


## RESULT
The program for creating To-do list using JavaScript is executed successfully.
