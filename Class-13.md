# Matplotlib
matplotlib is a python package for 2D-Graphics, it provides a quick way to visualize data from python and the ability to publish it in diffrent formates 

## pyplot 
pyplot provides a convenient interface to the matplotlib object-oriented plotting library. It is modeled closely after Matlab(TM). Therefore, the majority of plotting commands in pyplot have Matlab(TM) analogs with similar arguments. Important commands are explained with interactive examples.

### Making a simple plot 

drawing the cosine and sine function on the same plot 

first thing we will need to get the data for the sine and cosine functinos 

    ```
    import numpy as np 
    x = np.linespace(-np.pi,256,endpoint=True)
    C,S = np.cos(x), np.sin(x)

    ```
X is now a NumPy array with 256 values 
c is the cosin (256 values ) and s is the sine (256 values)

now matplotlib comes with a set of default settings that allow customizing all kinds of properties 

    ```
    plt.figure(figsize=(10,6),dpi =80)
    plt.plot(x,c,color ='blue',linewidth=2.5 , linestyle='-')
    plt.plot(x,s,color='red',linewidth=2.5 ,linestyle='-')

    ```

Current limits of the figure are a bit too tight and we want to make some space in order to clearly see all data points.

    ```
    plt.xlim(X.min()*1.1, X.max()*1.1)
    plt.ylim(C.min()*1.1, C.max()*1.1)

    ```
Current ticks are not ideal because they do not show the interesting values (+/-π,+/-π/2) for sine and cosine. We'll change them such that they show only these values.

    ``` 
    plt.xticks([-np.pi,-np.pi/2,0,np.pi/2,np.pi])
    plt.yticks([-1,0,+1])

    ```

we'll discard the top and right by setting their color to none and we'll move the bottom and left ones to coordinate 0 in data space coordinates.

    ```
    ax = plt.gca()
    ax.spines['right'].set_color('none')
    axe.spines['top'].set_color('none')
    ax.xaxis.set_ticks_postion('bototm')
    ax.spines['bottom'].set_postion(('data',0))
    ax.yaxis.set_ticks_postion('left')
    ax.spines['left'].set_postion(('data',0))

    ```

now lets add a legend to our graph in the upper corner 

    ```
    plt.plot(x,c,color='blue' , linewidth=2.5,linestyle="-" ,label =cosine)
    plt.plot(x,s,color='red',linewidth=2,5,linestyle="-",label=sine)
    plt.legend(loc='upper left',framon=Flase)

    ```


code snippts resoruce:

https://github.com/rougier/matplotlib-tutorial#quick-references