# Random Module 

Random module in python gives us acess to many oprations incuding maybe the most used one of them , generating random numbers 
we use the random function when we want to computer to pick a random number from a given range or random element from a list and so on...

here is a list of random module functions to generate random numbers with examples 

## Randinit 

    we use this to generate a random integer 
    example : 
    ```
    import random
    print(random.randit(0,5))
    #we import the random libary and use a built in method to generate a random number between 1 and 5 
    
    ```

## Random 

    if you want a large number u can multiply it
    lets say a random number between 0 and 1000 
    ```
    import random 
    random.random()*1000
    ```
## Choice 
 Generate a random value from a given sequence 

    ```
    import random 
    random.choice(['hi','bye','ok'])
    # you can also use it to give a random value from an already created list 
    some_list = [1,3,4,5,2,5,6,7,8]
    random.choice(some_list)

    ```
## Shuffle

 Shuffle changes the order of elements inside a list so end up in random order  

    ```  
    from random import shuffle
    x = [[i] for i in range]
    suffle(x)

    ```
    output

    ```
    # print x  gives  [[9], [2], [7], [0], [4], [5], [3], [1], [8], [6]]
    # of course your results will vary

    ```

## Randrange 
 this function generates a randomly selected element from a given range 

    ```
    randome.randrange(start,stop,step)

    ```

    example of use 

    ```
    import random 
    for i in range(3):
        print(random.randrange(0,101,5))
    ```

> Code snippts were taken from https://www.pythonforbeginners.com/random/how-to-use-the-random-module-in-python 

# Risk Analysis
  risk analysis is the process of identifying the risks in applications or software that you built and
 prioritizing them to test.After that, the process of assigning the level of risk is done. The categorization of the risks takes place, hence, the impact of the risk is calculated.

so why would we have risk analysis in software development ? 
In any software, using risk analysis at the beginning of a project highlights the potential problem areas. After knowing about the risk areas, it helps the developers and managers to mitigate the risks.

###  Possible risks that you could encounter 
* Use of new hardware
* Use of new technology
* Use of new automation tool
* The sequence of code
* Availability of test resources for the application

### Unavoidable risks
* The time that you allocated for testing
* A defect leakage due to the complexity or size of the application
* Urgency from the clients to deliver the project
* Incomplete requirements

### Risk magnitude indicators 
* High: means the effect of the risk would be very high and non-tolerable. The company might face loss.
* Medium: it is tolerable but not desirable. The company may suffer financially but there is a limited risk.
* Low: it is tolerable. There lies little or no external exposure or no financial loss.

## Risk Identification :

### Sets of risks 
* Business Risks: This risk is the most common risk associated with our topic. It is the risk that may come from your company or your customer, not from your project.
* Testing Risks: You should be well acquainted with the platform you are working on, along with the software testing tools being used.
* Premature Release Risk: a fair amount of knowledge to analyze the risk associated with releasing unsatisfactory or untested software is required
* Software Risks: You should be well versed with the risks associated with the software development process.


## Risk Assessment

 ![img](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2019/08/Picture1-528x290.png)




## How to perform Risk Analysis?
* Searching the risk
  
*  Analyzing the impact of each individual risk
  
* Measures for the risk identified



> Risk analysis rescource : https://www.edureka.co/blog/risk-analysis-in-software-testing/