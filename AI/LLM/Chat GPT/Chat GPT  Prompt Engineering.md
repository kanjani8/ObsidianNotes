Prompt patterns that are proven to get us better answers out of chat GPT
( from Vanderbilt universities Computer Science 's paper)

These patterns may be more or less effective depending on what you need 
So mix or alternate them until you find out where works better for your questions.

#### Persona Pattern

> [!Example] 
> if you wanted to review your code)
>you are going to pretend to be a senior engineer at a
Faang company review the following code
paying attention to security and performance provide output 
that a senior engineer would produce regarding the code 
(Don't mention a real person or people considered harmful(hacker?) )

> [! Example]
>  Pretend you're a marketing expert review the following slogans and
> suggest improvements based on other popular campaigns

#### Recipe pattern

this pattern is useful if you have something you want to accomplish
==you know the ingredients and sort of know the steps== to get there
but you need help putting them all together

this pattern is like telling Chat GPT 
you want to make a cake. You have flour water and sugar,
you know you have to mix those but you are not sure how,
on which order and what to do next.

> [!Example]
> I'm trying to write a Rust program to encrypt data.
> I know I have to read user input, validate it, encrypt it and return the encrypted data.
> Please provide a complete sequence of steps for me,
> fill in any missing steps, and identify any unnecessary steps 


> the "fill in any missing steps" statement:
> so Chat GPT fill in the gaps rather than asking us follow-up questions in case we missed something
   the "identify any unnecessary steps" statement: 
   it tells Chat GPT to find inaccuracies in our request to make the recipe better

#### Reflection Pattern
To always ==understand what the code is doing==,
using the reflection pattern,  you can ask Chat GPT
to explain the reasoning behind each answer
which will help you understand the output more
and can potentially help you catch the model 
in those times when it is hallucinating 

> [!Example]
> when you provide an answer, please explain the reasoning 
> and assumptions behind your answer.
> Explain your choices and address any potential limitations or edge cases 
> (and then ask your question )

 The answers will be more detailed and with more background information.

#### Refusal Breaker Pattern

When Chat GPT can't answer
because of ==knowledge limits, safety== or whatever 
this pattern is to sort of use Chat GPT against itself
by helping you reword or reframe the question that you want to ask 
so that it can be answered 

> [! Example]
> whenever you can't answer a question 
> explain why you can't answer the question.
> And Provide one or more alternative wordings 
> of the question that you could answer.
> (and then ask your question)

#### Flipping Interaction Pattern

==When it is difficult to structure the question== to Chat GPT
to make it provide all the required information.

==Making chatGPT ask us questions== until it accomplishes what we want
this pattern is useful when you know what you want
but you don't know the steps to get there 
and you don't know what information Chat GPT needs to help you get there

> [!Example]
> I want you to ask me questions to deploy a rust
> binary to a web server located in AWS.
> When you have all the information you need,
> Write a bash script to automate the deployment

after you run this query 
you will find Chat GPT asking you for the information it needs to help you 

Reference: https://www.youtube.com/watch?v=WRkig3VeRLY