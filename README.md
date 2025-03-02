# lab2

package lab2assignments;

public class Auto {

private String firstName, lastName, make, model;

private double liability, collision;

public void setAutoInfo(String firstName, String lastName, String make, String model, double liability, double collision) {

this.firstName = firstName;

this.lastName = lastName;

this.make = make;

this.model = model;

this.liability = liability;

this.collision = collision;

}

public double computeCommission() {

return (liability + collision) * 0.3; // 30% commission

}

public void printPolicy() {

System.out.println("\nAuto Policy");

System.out.println("-----------");

System.out.println("Name: " + firstName + " " + lastName);

System.out.println("Make: " + make);

System.out.println("Model: " + model);

System.out.printf("Liability: $%,.2f%n", liability);

System.out.printf("Collision: $%,.2f%n", collision);

System.out.printf("Commission: $%,.2f%n", computeCommission());

}

}

this is the code for home

package lab2assignments;

public class Home {

private String firstName, lastName;

private int squareFootage;

private double dwelling, contents, liability;

public void setHomeInfo(String firstName, String lastName, int squareFootage, double dwelling, double contents, double liability) {

this.firstName = firstName;

this.lastName = lastName;

this.squareFootage = squareFootage;

this.dwelling = dwelling;

this.contents = contents;

this.liability = liability;

}

public double computeCommission() {

return (dwelling + contents + liability) * 0.2; // 20% commission

}

public void printPolicy() {

System.out.println("\nHome Policy");

System.out.println("-----------");

System.out.println("Name: " + firstName + " " + lastName);

System.out.println("Footage: " + squareFootage);

System.out.printf("Dwelling: $%,.2f%n", dwelling);

System.out.printf("Contents: $%,.2f%n", contents);

System.out.printf("Liability: $%,.2f%n", liability);

System.out.printf("Commission: $%,.2f%n", computeCommission());

}

}

this is the code for life

package lab2assignments;

public class Life {

private String firstName, lastName;

private int age;

private double term;

public void setLifeInfo(String firstName, String lastName, int age, double term) {

this.firstName = firstName;

this.lastName = lastName;

this.age = age;

this.term = term;

}

public double computeCommission() {

return term * 0.2; // 20% commission

}

public void printPolicy() {

System.out.println("\nLife Policy");

System.out.println("-----------");

System.out.println("Name: " + firstName + " " + lastName);

System.out.println("Age: " + age);

System.out.printf("Term: $%,.2f%n", term);

System.out.printf("Commission: $%,.2f%n", computeCommission());

}

}

this is the code for the driver

package lab2assignments;

public class Driver {

public static void main(String[] args) {

CommissionCalculator calc = new CommissionCalculator();

calc.Run();

}

}

this is the calculator 

package lab2assignments;

import java.util.Scanner;

public class CommissionCalculator {

private Auto autoPolicy;

private Home homePolicy;

private Life lifePolicy;

private Scanner scanner;

public CommissionCalculator() {

autoPolicy = new Auto();

homePolicy = new Home();

lifePolicy = new Life();

scanner = new Scanner(System.in);

}

public void Run() {

while (true) {

System.out.println("\n-----------------------------");

System.out.println("Welcome to Parkland Insurance");

System.out.println("-----------------------------");

System.out.println("Enter any of the following:");

System.out.println("1) Enter auto insurance policy information");

System.out.println("2) Enter home insurance policy information");

System.out.println("3) Enter life insurance policy information");

System.out.println("4) Compute commission and print auto policy");

System.out.println("5) Compute commission and print home policy");

System.out.println("6) Compute commission and print life policy");

System.out.println("7) Quit");

int choice = getIntInput("\nChoice: ");

switch (choice) {

case 1:

enterAutoPolicy();

break;

case 2:

enterHomePolicy();

break;

case 3:

enterLifePolicy();

break;

case 4:

autoPolicy.printPolicy();

break;

case 5:

homePolicy.printPolicy();

break;

case 6:

lifePolicy.printPolicy();

break;

case 7:

System.out.println("Exiting Program...");

scanner.close();

return;

default:

System.out.println("Invalid choice. Please try again.");

}

}

}

private void enterAutoPolicy() {

System.out.println("\nEnter Auto Insurance Policy Information:");

String firstName = getStringInput("Enter first name: ");

String lastName = getStringInput("Enter last name: ");

String make = getStringInput("Enter make of vehicle: ");

String model = getStringInput("Enter model of vehicle: ");

double liability = getDoubleInput("Enter amount of liability: ");

double collision = getDoubleInput("Enter amount of collision: ");

autoPolicy.setAutoInfo(firstName, lastName, make, model, liability, collision);

}

private void enterHomePolicy() {

System.out.println("\nEnter Home Insurance Policy Information:");

String firstName = getStringInput("Enter first name: ");

String lastName = getStringInput("Enter last name: ");

int squareFootage = getIntInput("Enter house square footage: ");

double dwelling = getDoubleInput("Enter amount of dwelling: ");

double contents = getDoubleInput("Enter amount of contents: ");

double liability = getDoubleInput("Enter amount of liability: ");

homePolicy.setHomeInfo(firstName, lastName, squareFootage, dwelling, contents, liability);

}

private void enterLifePolicy() {

System.out.println("\nEnter Life Insurance Policy Information:");

String firstName = getStringInput("Enter first name: ");

String lastName = getStringInput("Enter last name: ");

int age = getIntInput("Enter age: ");

double term = getDoubleInput("Enter amount of term: ");

lifePolicy.setLifeInfo(firstName, lastName, age, term);

}

private int getIntInput(String prompt) {

while (true) {

System.out.print(prompt);

if (scanner.hasNextInt()) {

int value = scanner.nextInt();

scanner.nextLine();

return value;

}

System.out.println("Invalid input. Please enter a valid number.");

scanner.nextLine();

}

}

private double getDoubleInput(String prompt) {

while (true) {

System.out.print(prompt);

if (scanner.hasNextDouble()) {

double value = scanner.nextDouble();

scanner.nextLine();

return value;

}

System.out.println("Invalid input. Please enter a valid number.");

scanner.nextLine();

}

}

private String getStringInput(String prompt) {

System.out.print(prompt);

return scanner.nextLine();

}

}
