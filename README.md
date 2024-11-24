# angularnotes
my angular

# hello-world
- name says it all

Steps to Create "Hello World" in Angular
Create a New Angular Project:

ng new hello-world
You’ll be prompted to choose options like routing (select yes or no) and styles (e.g., CSS, SCSS). Choose as per your preference.

Open the src/app/app.component.html file.

Replace its content with:

<h1>Hello World</h1>

Optional Styling (if desired):

Open src/app/app.component.css or app.component.scss (depending on your choice during setup).

Add some styles:


h1 {
  color: blue;
  text-align: center;
  margin-top: 20%;
}


Summary of File Edits
app.component.html:

html

<h1>Hello World</h1>
app.component.css (optional):

css

h1 {
  color: blue;
  text-align: center;
  margin-top: 20%;
}


how to continue from that to "todo list"?

Building a "To-Do List" app with Angular is a great way to learn its basics. Here's how you can extend your "Hello World" app into a simple To-Do List:

Steps to Create a "To-Do List" in Angular

Set Up the To-Do List HTML: Update the app.component.html to include a form for adding tasks and a list to display tasks:

<div style="text-align: center;">
  <h1>To-Do List</h1>
  <form (ngSubmit)="addTask()">
    <input
      type="text"
      [(ngModel)]="task"
      name="task"
      placeholder="Enter a new task"
      required
    />
    <button type="submit">Add Task</button>
  </form>
  <ul>
    <li *ngFor="let item of tasks; let i = index">
      {{ item }}
      <button (click)="deleteTask(i)">Delete</button>
    </li>
  </ul>
</div>

Set Up the Component Logic: Update the app.component.ts file to handle adding and deleting tasks:

typescript

import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  task: string = '';
  tasks: string[] = [];

  addTask() {
    if (this.task.trim()) {
      this.tasks.push(this.task);
      this.task = '';
    }
  }

  deleteTask(index: number) {
    this.tasks.splice(index, 1);
  }
}

Add Two-Way Binding with FormsModule: To use [(ngModel)] for two-way binding, you need to import FormsModule.

Open the src/app/app.module.ts file.
Import FormsModule:

import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { FormsModule } from '@angular/forms';

import { AppComponent } from './app.component';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule, FormsModule],
  providers: [],
  bootstrap: [AppComponent],
})
export class AppModule {}
Add Basic Styling (Optional): Update app.component.css to style your to-do list:


form {
  margin-bottom: 20px;
}
input {
  padding: 8px;
  width: 200px;
}
button {
  margin-left: 10px;
  padding: 8px;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 5px 0;
}
li button {
  margin-left: 10px;
  background-color: red;
  color: white;
  border: none;
  cursor: pointer;
}
li button:hover {
  background-color: darkred;
}

Run the Application: Start the server and check your work:

You can add tasks by typing in the input and clicking the "Add Task" button.
You can delete tasks by clicking the "Delete" button next to each task.
Summary
New Features Added:
Two-way data binding using [(ngModel)].
Dynamic rendering of tasks using *ngFor.
Event handling with (ngSubmit) and (click).
This creates a fully functional to-do list app using Angular. 🎉





