# To-Do-List
A Simple To-Do List application is a simple yet functional web app that allows users to add, manage, and remove tasks

<!DOCTYPE html>
<html>

<head> 

</head>

<body>
    <div class="container">
        <h1>To-Do List</h1>
        <div class="task-input">
            <input type="text" id="taskInput" placeholder="Enter a new task...">
            <button id="addTaskButton">Add Task</button>
        </div>
        <ul id="taskList"></ul>
    </div>
</body>

</html>

#CSS
body {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background-color: #f0f0f0;
    font-family: Arial, sans-serif;
}

.container {
    width: 100%;
    max-width: 400px;
    text-align: center;
    background-color: #ffffff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
}

h1 {
    color: #333;
    margin-bottom: 20px;
}

.task-input {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
}

.task-input input {
    width: 70%;
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ddd;
    border-radius: 4px 0 0 4px;
}

.task-input button {
    padding: 10px 20px;
    font-size: 16px;
    border: none;
    background-color: #28a745;
    color: #fff;
    cursor: pointer;
    border-radius: 0 4px 4px 0;
}

#taskList {
    list-style-type: none;
    padding: 0;
}

.task-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    background-color: #f9f9f9;
    margin-bottom: 8px;
    border-radius: 4px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.completed {
    text-decoration: line-through;
    color: #888;
}

.delete-btn {
    background-color: #dc3545;
    color: #fff;
    border: none;
    padding: 5px 10px;
    cursor: pointer;
    border-radius: 4px;
}

#JS
const addTaskButton = document.getElementById('addTaskButton');
const taskInput = document.getElementById('taskInput');
const taskList = document.getElementById('taskList');

addTaskButton.addEventListener('click', addTask);

function addTask() {
    const taskText = taskInput.value.trim();

    if (taskText === "") {
        alert("Please enter a task!");
        return;
    }

    const taskItem = document.createElement('li');
    taskItem.classList.add('task-item');

    const checkbox = document.createElement('input');
    checkbox.type = 'checkbox';
    checkbox.addEventListener('click', () => {
        taskItem.classList.toggle('completed');
    });

    const taskName = document.createElement('span');
    taskName.textContent = taskText;

    const deleteButton = document.createElement('button');
    deleteButton.textContent = 'Delete';
    deleteButton.classList.add('delete-btn');
    deleteButton.addEventListener('click', () => {
        taskList.removeChild(taskItem);
    });

    taskItem.appendChild(checkbox);
    taskItem.appendChild(taskName);
    taskItem.appendChild(deleteButton);
    taskList.appendChild(taskItem);

    
    taskInput.value = '';
}
