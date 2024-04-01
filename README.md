I'll explain my code

**import math
import matplotlib.pyplot as plt
import numpy as np**

These lines import the necessary libraries: math for mathematical functions, matplotlib.pyplot for plotting graphs, and numpy for numerical computations. 
 
**def solve_expr(x_values, expr): 
    y_val = [max(0, expression(x)) for x in x_values]
    return y_val**

This function solve_expr takes a list of x values x_values and an expression expr (a lambda function), and computes the corresponding y values by applying the expression to each x value. It uses a list comprehension to iterate over the x values, computing the expression value for each x, and taking the maximum between 0 and the expression value. This is done to ensure that the plotted graph doesn't go below y=0.

**def write_to_file(x_values, y_val_dict):
    with open("output_values.txt", "w") as file:
        for expression_name, values in y_val_dict.items():
            file.write(f"{expression_name}:\n")
            for value in values:
                file.write(f"{int(round(value))}\n")  # Write rounded integer value
            file.write("\n")**
            
This function write_to_file takes a list of x values x_values and a dictionary y_val_dict containing expression names as keys and corresponding y values as values. It writes these values to a file named "output_values.txt". For each expression, it writes the expression name followed by its y values, rounded to the nearest integer.            

**def plot_expression(x_values, y_val, expression_name):
    plt.figure(figsize=(12, 8))
    plt.plot(x_values, y_val, label=expression_name, linewidth=2, color='blue')
   
    plt.title(f"Graph of {expression_name}")
    plt.xlabel('x')
    plt.ylabel('y')
    plt.xlim(left=0)
    plt.ylim(bottom=0)
    plt.legend(loc='upper left')
    plt.grid(True)
    plt.show()**

    This function plot_expression takes a list of x values x_values, a list of y values y_val, and a string expression_name. It plots the graph of the given expression using Matplotlib, with the provided x and y values. It sets the title, labels for x and y axes, limits for x and y axes, legend, and grid, and then shows the plot.

    **def plot_all_expressions(x_values, y_values_dict):
    plt.figure(figsize=(12, 8))
   
    for expression_name, y_val in y_val_dict.items():
        plt.plot(x_values, y_val, label=expression_name, linewidth=2)
   
    plt.title("Graph of All Expressions")
    plt.xlabel('x')
    plt.ylabel('y')
    plt.xlim(left=0)
    plt.ylim(bottom=0)
    plt.legend(loc='upper left')
    plt.grid(True)
    plt.show()**

    This function "plot_all_expressions" takes a list of x values "x_values" and a dictionary "y_val_dict" containing multiple expressions' y values. It plots all the expressions in one graph using Matplotlib, with the provided x and y values. It sets the title, labels for x and y axes, limits for x and y axes, legend, and grid, and then shows the plot.

The remaining part of the code defines expressions as lambda functions, prompts the user to choose an expression to plot, and handles the user input to plot the selected expression or all expressions. It then calls the appropriate functions to plot and write the results to a file.

