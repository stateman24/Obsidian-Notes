---
Author: Kathy Sierra, Bert Bates, Trisha Gee
Status:
  - "In progress "
Type: Book
Rating: ⭐⭐⭐⭐⭐
Expected Completion Date: 2024-12-31
---
> [!important]  
> Notion Tip: Use this page to keep track of all your notes and highlights. You can also reference other Notion pages by typing the [[ command. Learn more here.  

  

[![](https://www.notion.so)](https://www.notion.so)

[Notes](#Notes)

[Key takeaways](#Key takeaways)

[Quotes](#Quotes)

[Summary](#Summary)

# Note

## Chapter 5
### Bullet Points
- Your Java program should start with a high-level design.
- Typically you’ll write three things when you create a new class: 
  -  prep code  
  - test code  
  - real (Java) code 
- Prep code should describe what to do, not how to do it. Implementation comes later.
- Use the prep code to help design the test code.
- A class can have one superclass only.
- Write test code before you implement the methods.
- Choose for loops over while loops when you know how many times you want to repeat the loop code.
- The enhanced for loop is an easy way to loop over an array or collection.
- Use the increment operator to add 1 to a variable (x++;).
- Use the decrement operator to subtract 1 from a variable (x--;).
- Use break to leave a loop early (i.e., even if the boolean test condition is still true).
### Important Notes
####  Test Driven Development 
It is a programming concept that started 1999 under Extreme Programming (XP) software development methodology world. One of the central ideas in XP was to write test code before writing the actual code. 
- [ ]  **Book to check**: Driven Development: By Example by Kent Beck ⏬
Here is a partial list of key ideas in TDD:
- Write the test code first.
- Develop in iteration cycles.
- Keep it (the code) simple
- Refactor (improve the code) whenever and wherever you notice the opportunity.
- Don’t release anything until it passes all the tests.
- Don’t put in anything that’s not in the spec (no matter how tempted you are to put in functionality “for the future”).
- No killer schedules; work regular hours.
Three things to do when writing a Java class
1. Write prep code: It is a pseudo code 
2. Write a test Code
3. Write the actual code 
##### Difference between `for` and `while` loop in java
`while` loop use boolen test and does not have initialization and execution phase as for loop. It good for cases where the amount of iteration is not know and what to keep going until a certain condition is meet. Whereas `for` loop is good for known amounts of loops.
### Key Code Snippets
#### Sytanx for for loop when looping through an array of objects 
```java
for(int cell : numCells){
 // Some code
} // The `:` is like "for in" in java
```

```java
int x = 0; z = ++x // it means increment x and use the value i.e z is 1 and x is 1

int x = 0; z = x++ // it mean use x and then increment x i.e z is 0 and x is 1

(int) // It is a cast operator to shove big bits to small ones e g. long to int
```
# Key takeaways

# Quotes

# Summary