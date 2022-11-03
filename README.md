# IEM 5003 Programming Assignment

A more interactive version of these Instructions are available at this [link](https://www.notion.so/IEM-5003-Programming-Assignment-fb54e36b75fa4b69a1a2eba259ae7249)

### Code Components

This repository contains code designed to help you finish the Programming Assignment for IEM 5003. It consists of the following folders:

- `data`
    
    This folder contains the data needed to run the Python code. Specifically, it has the datasets `sensor_loc` and `wine_quality`. Both data sets have been provided in the CSV format and comprise of a training and a testing datasets as well. 
    
    Explore the data carefully before beginning the project. 
    
- `example_images`
    
    This folder contains some example images in their most basic form to give you an idea of how your output plots of graphs must look like. It is not necessary to use the same image formatting at all. Feel free to use different colors, markers, sizes etc. However, the core insight being represented by the data must look like as shown in these images.
    
- `example_reports`
    
    This folder contains examples of the output reports from the running the Python code. The reports contain various aspects of the Logistic and Linear Regression models for each of the cases. It contains dummy values but this is to give you an idea of how your output must look like. 
    

The repository also contains the following files:

- `Driver.py`
    
    **This is the main file that you need to run and will be interacting with. Ensure that you only interact with the required functions in this file. Do not tamper with the code in lines that are not inside a function.** You will need to populate the following functions.
    
    - `sensorLocPredictionErrorHistogram(lin1_y_test_pred_err)`: Plots the prediction error for the `sensor_loc` dataset
    - `linearAndLogisticRegressionErrorComparison``(lin_y_test_pred_err,log_y_test_pred_err)`:  Plots the prediction error for the `wine_quality` dataset for both linear and logistic regression.
    - `visualizeChlorineSulphateScatterPlot(X,path)`: Plots the chlorine Sulphate Scatter plot.
    - `visualizeCitricAcidBoxPlot(X,path)` : Plots the Citric Acid BoxPlot.
    - `visualizeDensityHistogram(X,path)` : Plots the Density Histogram Plot.
- `LinearRegression.py`
    
    This is the file which is responsible for carrying out LinearRegression. Read the file carefully. You are required to populate the following functions:
    
    - `linearRegression(self,X,y)` : This consumes the data points `X` and `y` which comes from the `evaluateRegressor` function. You are required to do the following steps:
        - Do linear regression using any Python package.
        - Obtain the coefficient of determination/score/R^2 value.
        - Obtain the regression parameters
        - Calculate predicted values
        
        The function must output four values:
        
        - `reg` : This is the Python object that holds the regression model. This must have a utility like `reg.predict(X)`.
        - `score` : This is the R2 value.
        - `params` : This is the parameters of the model.
        - `y_pred` : This is the prediction of y on test data.
    - `computeResiduals(self,y_pred,y)` : This function must compute the residuals given `y_pred` and `y` and output the `residuals` vector.
    - `computeSSE(self,residuals)`: This function computes the SSE score given the residual vector and returns it using the variable `SSE`
    - `computeSSR(self,y_pred,y)`: This function must compute the SSR given `y_pred` and `y` and return the SSR using the variable `SSR`
    - `computeFScore(self,alpha,k,n,p)`: This function computes the F-Score by taking as input the following values:
        - `alpha`: The level of significance
        - `k` : The number of regression parameters.
        - `p` : The number of parameters to estimate.
        - `n`: The total number of rows.
        
        The function returns the the F Score in the variable `f`
        
    - `computeFTestStatistic(self,y_pred,y,residuals,alpha,k,n,p)` : This function computes the F test statistic by taking as input the following values:
        - `y_pred` : The predictor that the code learnt before.
        - `y` : The response variable.
        - `residuals` : The residual value computed before.
        - `alpha`: The level of significance
        - `k` : The number of regression parameters.
        - `p` : The number of parameters to estimate.
        - `n`: The total number of rows.
        
        The function returns the the F Score in the variable `f`. 

        💡 **Keep in mind that you would need to use the functions `computeSSE` and `computeSSR` inside this function in order to compute the F statistic.**
        
    - `computepValue(self,test_statistic,alpha,k,n,p)` : This function computes the p-value given the test statistic provided in `computeFTestStatistic` by taking as input the following values:
        - `test_statistic` : The F test statistic.
        - `alpha`: The level of significance
        - `k` : The number of regression parameters.
        - `p` : The number of parameters to estimate.
        - `n`: The total number of rows.
        
        The function returns the p-value stored in the variable `p-value`
        
    - `predictNewObservations(self,lin_reg,X)`: This function must compute the predictions using the `lin_reg` object obtained from the `linearRegression` function. It takes as input the following variables:
        - `X` : This is the the X values on which you would need to predict on.
        - `lin_reg` : The Python Regression object obtained from the `linearRegression` function.
        
        The function must return `y_test_pred` which contains the output of the prediction. 
        
    - `LogisticRegression.py`
        
        This is the file which is responsible for carrying out Logistic Regression. Read the file carefully. You are required to populate the following functions:
        
        - `logisticRegression(self,X,y)` : This consumes the data points `X` and `y` which comes from the `evaluateRegressor` function. You are required to do the following steps:
            - Do linear regression using any Python package.
            - Obtain the coefficient of determination/score/R^2 value.
            - Obtain the regression parameters
            - Calculate predicted values
            
            The function must output four values:
            
            - `reg` : This is the Python object that holds the regression model. This must have a utility like `reg.predict(X)`.
            - `score` : This is the R2 value.
            - `params` : This is the parameters of the model.
            - `y_pred` : This is the prediction of y on test data.
        - `computeResiduals(self,y_pred,y)` : This function must compute the residuals given `y_pred` and `y` and output the `residuals` vector.
        - `computepValue(self,test_statistic,alpha,k,n,p)` : This function computes the p-value given the test statistic provided in `computeFTestStatistic` by taking as input the following values:
            - `test_statistic` : The F test statistic.
            - `alpha`: The level of significance
            - `k` : The number of regression parameters.
            - `p` : The number of parameters to estimate.
            - `n`: The total number of rows.
            
            The function returns the p-value stored in the variable `p-value`
            
        - `predictNewObservations(self,lin_reg,X)`: This function must compute the predictions using the `lin_reg` object obtained from the `linearRegression` function. It takes as input the following variables:
            - `X` : This is the the X values on which you would need to predict on.
            - `lin_reg` : The Python Regression object obtained from the `linearRegression` function.
            
            The function must return `y_test_pred` which contains the output of the prediction. 
            

### Instructions to run

Download the code from Github using the following commands
`git clone https://github.com/paritoshpr/IEM5003Project.git`

Alternately you can simply download a `.zip` file from the [Github Link](https://github.com/paritoshpr/IEM5003Project.git) 

Run the code using `python Driver.py` and you must see the images and the reports appear in the same folder that you are running the code from.

### Deliverables

You must submit 1 single `.pdf` file containing the following images:

- `ChlorineSulphateScatterPlot.pdf`
- `CitricAcidBoxPlot.pdf`
- `DensityHistogram.pdf`
- `SensorLocLinearRegressionError.pdf`
- `WineQualityLinearRegressionError.pdf`
- `WineQualityLogisticRegressionError.pdf`
- A 1 paragraph (2-3 sentences/lines) description of your observations of each of the above image.
- Report summaries from the following files:
    - `LinearRegression_sensor_loc.txt`
    - `LinearRegression_wine_quality.txt`
    - `LogisticRegression_wine_quality.txt`

### Other Tips and Suggestions

Take a look at the [scikit-learn](https://scikit-learn.org/stable/) library available for Python. For statistical testing, take a look at [scipy](https://docs.scipy.org/doc/scipy/reference/stats.html). Depending on your local Python environment, you might need to install various libraries. You can do that using `pip install <library_name>`

A popular option is to leverage Anaconda/Miniconda and creating a virtual environment. Please take a look at [https://www.anaconda.com/products/distribution](https://www.anaconda.com/products/distribution) .

💡 **You could run, edit and develop the code in multiple ways. Either you can use an IDE such as [PyCharm](https://www.jetbrains.com/pycharm/), or [Visual Studio](https://visualstudio.microsoft.com/vs/features/python/). You could use a Jupyter notebook to run and edit code.  Or you can use [Google Colab](https://colab.research.google.com/) to run your experiments.**


