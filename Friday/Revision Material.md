#JAVASCRIPT
```JS

var shoppingList = [];

console.log("hello world");

function addItem(item) {
    shoppingList.push(item);
    console.log(item + " has been added to your shopping list.");
}

function removeItem(index) {
    if (index >= 0 && index < shoppingList.length) {
        var removedItem = shoppingList.splice(index, 1);
        console.log(removedItem[0] + " has been removed from your shopping list.");
    } else {
        console.log("Error");
    }
}


function displayItems() {
    for (var i=0; i<shoppingList.length; i++) {
        console.log(i + ": " + shoppingList[i]);
    }
}

function clearList() {
    shoppingList = []; 
    console.log("The shopping list has been cleared.");
}


addItem("Apples");
addItem("Bread");
addItem("Milk");
displayItems();
removeItem(1); 
displayItems();
clearList();
```
---
```JS
//prompt-sync is used through node.js

const prompt = require("prompt-sync")();

let taskList = [];

function addtask() {
    let task = prompt("Enter Task: ");
    taskList.push(task);
    console.log(task + " added");
}

function removetask() {
    let index = parseInt(prompt("Enter index of task to remove: "));
    if (index >= 0 && index < taskList.length) {
        let removedTask = taskList.splice(index, 1);
        console.log(removedTask + " removed");
    } else {
        console.log("Incorrect Index");
    }
}

function displayTasks() {
    for (let i = 0; i < taskList.length; i++) {
        console.log(i+1 + ": " + taskList[i]);
    }
}

function clearTasks() {
    taskList = [];
    console.log("All tasks cleared");
}

let input;
while (input !== "exit") {
    console.log("Enter the function you want to perform: [add - to add task], [remove - to remove task], [display - to display all tasks], [clear - to clear all tasks], [exit - to exit]");
    input = prompt("Enter: ");
    
    console.clear();
    
    if (input === "add") {
        addtask();
    } else if (input === "remove") {
        removetask();
    } else if (input === "display") {
        displayTasks();
    } else if (input === "clear") {
        clearTasks();
    } else if (input !== "exit") {
        console.log("Please enter an appropriate command");
    }
}

console.log("Exiting the program.");

```
---
```JS
var employees= [

{name : "1",salary : 20},

  

]

  

function addEmployee(name, salary){

var newEmployee={

name : name,

salary : salary,

};

employees.push(newEmployee);

}

  

function updatePerf(index , newSalary){

employees[index].salary = newSalary;

}

  

function displayEmp(){

for(i=0 ; i<employees.length ; i++){

console.log(employees[i].name);

console.log(employees[i].salary);

}

}

  

addEmployee("2", 30);

displayEmp();

addEmployee("3", 40);

displayEmp();

```
---
```JS
var products = [];

  

function productAdd(iname, iquantity, iprice){

var product = {

name : iname,

quantity : iquantity,

price : iprice,

};

products.push(product);

console.log("Product Added");

}

  

function display(){

for(i=0 ; i<products.length ; i++){

console.log(products[i].name);

console.log(products[i].quantity);

console.log(products[i].price);

}

}

products.splice()

  

productAdd("1",3,4);

display();

```
---
OPP
```C++

#include <iostream>

#include <string>

  

class LibraryBook{

private:

int availableCopies;

public:

std::string name;

std::string author;

long isbn;

  

void setCopies(int copies){

availableCopies = copies;

}

  

int getCopies(){

return availableCopies;

}

  

void displayDetails(){

std::cout<<"Title:"<<name<<std::endl<<"Author"<<author<<std::endl<<"ISBN"<<isbn<<std::endl<<"Copies"<<availableCopies<<std::endl;

}

};

  

int main(){

LibraryBook book1;

std::cout<<"Enter Book Name:";

std::cin>>book1.name;

std::cout<<"Enter Author Name:";

std::cin>>book1.author;

std::cout<<"Enter ISBN:";

std::cin>>book1.isbn;

int copies;

std::cout<<"Enter copies:";

std::cin>>copies;

book1.setCopies(copies);

book1.displayDetails();

  
  

}
```
---
```C++
#include <iostream>

#include <string>

  

class Animal{

private:

std::string name;

int age;

public:

  

void inputName(std::string name){

this->name = name;

}

std::string getName(){

return name;

}

void inputAge(int age){

this->age = age;

}

int getAge(){

return age;

}

  

void displayInfo(){

std::cout<<"Name: "<<name<<std::endl<<"Age: "<<age<<std::endl;

}

  

};

  

class Mammal : public Animal{

  

public:

void feedBaby(){

std::cout<<"Feeding"<<std::endl;

}

};

  

class Bird : public Animal{

  

public:

void layEgg(){

std::cout<<"Laying"<<std::endl;

}

};

  

class Reptile : public Animal{

  

public:

void shed(){

std::cout<<"Shedding"<<std::endl;

}

};

  
  

int main(){

Mammal m1;

m1.inputName("Mammal");

m1.inputAge(2);

m1.displayInfo();

m1.feedBaby();

  

Bird b1;

Reptile r1;

  
  
  

}
```
---
```c++

#include <iostream>

#include <string>

  

class Person{

private:

std::string name;

int age;

public:

std::string inputName(std::string name){

this->name = name;

}

void getName(){

std::cout<<name<<std::endl;

}

int inputAge(int age){

this->age = age;

}

void getAge(){

std::cout<<age<<std::endl;

}

virtual void displayInfo(){

std::cout<<"Name"<<name<<std::endl<<"Age"<<age<<std::endl;

}

};

  

class Employee : public Person{

private:

int employeeID;

public:

int getID(){

return employeeID;

}

void setID(int id){

employeeID = id;

}

  

void displayInfo() override{

std::cout<<"Employee ID"<<employeeID<<std::endl;

}

};

  

int main(){

  

}
```
---
```C++
#include <iostream>

#include <string>

  

class BankAccount{

private:

std::string acntNum;

double balance;

public:

BankAccount(){

acntNum = "1234";

balance = 0;

}

  

void deposit(double amount){

balance += amount;

}

  

void withdraw(double amount){

if(amount<=balance){

balance -= amount;

std::cout<<"Amount $ Has been Deducted"<<amount<<std::endl;

std::cout<<"Current Balance is now:"<<balance<<std::endl;

  

} else if (amount>=balance){

std::cout<<"Not Enough Balance"<<std::endl;

}

}

  

void checkBalance(){

std::cout<<"Current Balance: "<<balance<<std::endl;

}

  

};

  

int main(){

  

}
```
---
```c++
#include <iostream>

#include <string>

  

class Bill{

protected:

double amount;

public:

virtual void displayDetails(){

std::cout<<"Amount:"<<amount<<std::endl;

}

};

  

class InpatientBill : public Bill{

protected:

std::string patientID;

std::string roomType;

int daysAdmitted;

public:

void setDetails(int amount, std::string patientID, std::string roomType, int days){

this->amount = amount;

this->patientID = patientID;

this->roomType = roomType;

daysAdmitted = days;

}

  

void displayDetails() override{

// public::displaydetails();

std::cout<<"In-Patient Details"<<std::endl;

std::cout<<"Amount:"<<amount<<std::endl;

std::cout<<"Patient ID:"<<patientID<<std::endl;

std::cout<<"Room Type"<<roomType<<std::endl;

std::cout<<"Days:"<<daysAdmitted<<std::endl;

}

};

  

class OutpatientBill : public Bill{

protected:

std::string patientID;

int docCharges;

int labCharges;

public:

void setDetails(int amount, int docCharges, int labCharges, int days){

this->amount = amount;

this->patientID = patientID;

this->docCharges = docCharges;

this->labCharges = labCharges;

}

  

void displayDetails() override{

std::cout<<"Out-Patient Details"<<std::endl;

std::cout<<"Amount:"<<amount<<std::endl;

std::cout<<"Patient ID:"<<patientID<<std::endl;

std::cout<<"Doc Charges:"<<docCharges<<std::endl;

std::cout<<"Lab Charges:"<<labCharges<<std::endl;

}

};

  

int main(){

  

}

```
---
```

```