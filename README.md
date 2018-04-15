import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'app';

  
  public todoList: any[] = [
    {
      value: 'Hit the gym',
      status: false
    },
    {
      value: 'Pay bills',
      status: true
    },
    {
      value: 'Meet George',
      status: false
    }
  ];
  public inputValue: string;
  public filterValue: string = "";
  public tempList: any[] = this.todoList;

  addTodo() {
    if(this.inputValue) {
      var newTodo = {
        value: this.inputValue,
        status: false
      }
      this.todoList.push(newTodo);
      this.tempList = this.todoList;
      this.inputValue = "";
    }
    
  }

  toggleClick(item) {
    item.status = !item.status;
  }

  todoFilter() {
    this.tempList = [];
    if(this.filterValue === "true") {
      for(let item of this.todoList) {
        if(item.status === true) {
          this.tempList.push(item);
        }
      }
    } else if(this.filterValue === "false") {
      for(let item of this.todoList) {
        if(item.status === false) {
          this.tempList.push(item);
        }
      }
    }else {
      this.tempList = this.todoList;
    }
  }

  delTodo(item) {
    var index = this.todoList.indexOf(item);
    this.todoList.splice(index, 1);
  }
}
