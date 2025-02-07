# To-Do List 📝

## Description
A simple and user-friendly To-Do List application built using HTML, CSS, and JavaScript. This project allows users to create, manage, and store task lists locally in their browser.

## Features
- ➕ Add tasks effortlessly.
- ✅ Mark tasks as completed.
- ❌ Delete tasks with a single click.
- 💾 Persistent task storage using **LocalStorage**.

## Demo
Link - https://harjotrocks.com/javascript/to-do-list/

## Technologies Used
- **📝 HTML**: Structure of the application.
- **🎨 CSS**: Styling for layout and design.
- **🤖 JavaScript**: Handles task management logic and data storage.

## How to Use
1. 📂 Clone the repository or download the files.
2. 🗃️ Open `index.html` in a web browser.
3. ✏️ Enter a task in the input box.
4. ➕ Click the **Add** button to create a task.
5. ✅ Click on a task to mark it as completed.
6. ❌ Click the cross (`×`) next to a task to delete it.
7. 🔄 Refresh the page — your tasks will persist thanks to **LocalStorage**.

## Code Explanation
### 📚 HTML
Defines the basic structure of the application with the following elements:
- **Input Field:** Captures user input for tasks.
- **Add Button:** Triggers the creation of a new task.
- **Task List:** Displays tasks with options to check or delete them.

### 🎨 CSS
- Provides clean and simple styling for the UI.
- Highlights completed tasks and organizes task layout.

### 💻 JavaScript
#### Variables and Selectors
```javascript
const inputBox = document.getElementById("input-box");
const listContainer = document.getElementById("list-container");
```
- **`inputBox`**: Captures user input.
- **`listContainer`**: Holds the list of tasks.

#### Functions
```javascript
function addTask() {
    if (inputBox.value === '') {
        alert("Please write something");
    } else {
        let li = document.createElement("li");
        li.innerHTML = inputBox.value;
        listContainer.appendChild(li);
        let span = document.createElement("span");
        span.innerHTML = "\u00d7";
        li.appendChild(span);
    }
    inputBox.value = "";
    saveData();
}
```
- **`addTask`**: Adds a new task if the input is not empty.

```javascript
listContainer.addEventListener("click", function (e) {
    if (e.target.tagName === "LI") {
        e.target.classList.toggle("checked");
        saveData();
    } else if (e.target.tagName === "SPAN") {
        e.target.parentElement.remove();
        saveData();
    }
}, false);
```
- **Event Listener:** Handles task completion and deletion.

```javascript
function saveData() {
    localStorage.setItem("data", listContainer.innerHTML);
}

function showTask() {
    listContainer.innerHTML = localStorage.getItem("data");
}

showTask();
```
- **`saveData`**: Saves tasks to LocalStorage.
- **`showTask`**: Loads tasks from LocalStorage when the page is refreshed.


## Improvements
- 🌟 Add task categories or tags.
- 📅 Implement due dates for tasks.
- 🌐 Enable syncing across multiple devices.


