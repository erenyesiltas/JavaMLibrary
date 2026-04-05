# JavaMLibrary
This project was created to develop self-coding and statistical skills in the field of machine learning using Java. I learned statistical methods for machine learning in a course I took at university, and I wanted to improve myself by applying these fundamentals to Java. Even with artificial intelligence and standardized libraries, in a scenario where the internet and everything else were to disappear one day, having the ability to build these things from scratch is crucial.

User Guidance;
If you want to examine my code you can download rar arcihve. Otherway you can download .jar file to directly try it.

First implement required imports import jar file to your class path
then import library.

import com.derivasoftware.eduML.*;

and create an arrayList (type Double) for both x and y values. I used arraylists to store datas. In the next time I want to create my data preprocessing library.

LinearRegression class;

create object;
LinearRegression reg = new LinearRegression();

model fitting;

X denotes X dataset
y denotes y dataset
0.70 denotes train test splitting rate

reg.fit(X,y,0.70);

## Evaluation
reg.MAE(); return double value for mean absolute error.
reg.MSE(); return double value for mean squared error.
reg.RMSE(); return double value for root mean squared error.
reg.predict(x); return predicted y value for x

reg.R2Score(); return double value for r score






## Example code;

package deneme;
import java.util.ArrayList;
import java.util.Arrays;

import com.derivasoftware.eduML.*;

public class main {

	public static void main(String[] args) {
		
		LinearRegression reg = new LinearRegression();
		
		ArrayList<Double> X_new = new ArrayList<>();
		ArrayList<Double> y_new = new ArrayList<>();

		
		double[] x_vals = {
		    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20,
		    21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40,
		    41, 42, 43, 44, 45, 46, 47, 48, 49, 50
		};

		double[] y_vals = {
		    485.2, 470.1, 455.8, 440.3, 425.9, 410.2, 395.5, 380.1, 365.4, 350.9,
		    335.2, 320.7, 305.1, 290.4, 275.8, 260.2, 245.9, 230.3, 215.1, 200.7,
		    185.4, 170.9, 155.2, 140.6, 125.1, 110.8, 95.3, 80.7, 65.2, 50.9,
		    35.4, 20.1, 5.8, -9.2, -24.5, -40.1, -55.6, -70.2, -85.8, -100.4,
		    -115.1, -130.7, -145.2, -160.8, -175.4, -190.1, -205.7, -220.2, -235.8, -250.4
		};

		for(int i=0; i<50; i++) {
		    X_new.add(x_vals[i]);
		    y_new.add(y_vals[i]);
		}
		
		 reg.fitModel(X_new, y_new,0.7);
	        System.out.println(reg.predict(8)); 
	        System.err.println(reg.MAE()); 
	        System.err.println(reg.MSE()); 
	        System.err.println(reg.RMSE()); 
	     
	        String greenCode = "\u001B[32m";
	        String defaultCode = "\u001B[0m";

	        
	        System.out.println(greenCode + String.format("%.8f", reg.R2Score()) + defaultCode);

	}

}


## Polynomial Regression
package com.derivasoftware.eduML;
import java.util.ArrayList;
import java.util.Arrays;

import com.derivasoftware.eduML.LinearRegression;

public class App 
{
    public static void main( String[] args )
    {
       
        LinearRegression reg = new LinearRegression();
        ArrayList<Double> X_tr = new ArrayList<>(Arrays.asList(
        	    -1.282, 0.425, 1.953, 2.625, -1.426, -1.311, 2.823, 2.346, 1.210, -2.631, 
        	    2.794, 1.449, 0.490, 2.409, 0.072, -1.602, -0.761, 2.882, 0.853, 1.887,
        	    -0.865, -1.321, 1.607, -2.705, -1.580, -2.121, 0.893, -2.742, 1.191, 1.386,
        	    2.779, -2.625, -0.425, -0.387, -0.751, 1.265, 0.142, -0.335, 0.893, -2.992,
        	    1.321, -2.277, -2.042, -2.671, 2.334, -1.933, -0.029, 0.826, 0.123, -0.572,
        	    -2.851, 1.910, -2.193, 2.986, 0.891, -1.145, 0.114, -1.282, -1.446, -2.315,
        	    1.411, 0.664, 1.661, -2.914, -2.843, 2.219, -2.502, -0.836, -1.794, -1.070,
        	    0.766, 2.696, -2.243, -0.763, 1.668, 0.537, 0.166, -0.633, 1.541, 1.584,
        	    -0.735, 1.806, -1.891, 2.735, 0.785, -2.159, 0.616, -0.743, 1.863, -0.066,
        	    -2.198, 0.103, -0.483, 0.810, 0.033, 2.055, 0.864, -1.586, 1.558, 0.512
        	));
        
        ArrayList<Double> y_tr = new ArrayList<>(Arrays.asList(
        	    1.010, 2.281, 4.415, 10.563, 0.627, -1.068, 9.011, 8.508, 3.713, 1.090,
        	    8.632, 5.135, 2.513, 8.962, 1.860, -0.192, 1.528, 10.724, 2.236, 7.088,
        	    1.460, 0.679, 6.072, -0.294, 1.411, 1.886, 4.114, 2.525, 4.251, 5.194,
        	    9.883, 1.367, 0.446, 1.560, 1.474, 5.058, 2.762, 0.954, 3.986, 2.775,
        	    4.422, -0.281, 1.705, 2.175, 7.051, 0.303, 1.267, 3.998, 2.184, 1.654,
        	    3.862, 9.121, 1.187, 11.000, 3.666, 0.702, 2.914, 2.107, 0.285, 1.504,
        	    5.931, 4.525, 4.632, 2.483, 2.901, 6.561, 2.087, -0.978, -0.067, -0.547,
        	    3.665, 9.118, 0.201, 1.797, 7.276, 3.668, 2.788, 0.672, 3.505, 6.677,
        	    1.830, 5.529, 2.506, 9.729, 2.530, 3.088, 2.735, 1.858, 5.181, 2.026,
        	    0.837, 2.903, 2.995, 3.127, 1.510, 8.686, 3.901, 0.786, 5.447, 4.356
        	));
        reg.fitModel(X_tr, y_tr,0.7);
        System.out.println(reg.predict(0.2)); 
        System.err.println(reg.MAE()); 
        System.err.println(reg.MSE()); 
        System.err.println(reg.RMSE()); 
     
        String greenCode = "\u001B[32m";
        String defaultCode = "\u001B[0m";

        
        System.out.println(greenCode + String.format("%.8f", reg.R2Score()) + defaultCode);
        System.out.println(greenCode + String.format("%.8f", reg.R2ScoreVal()) + defaultCode);
        PolynomialRegression polReg = new PolynomialRegression(10);
        polReg.fitModel(X_tr, y_tr, 0.80);
        System.out.println(polReg.predict(0.4)); 
        System.err.println(polReg.MSE()); 
        System.err.println(polReg.MAE());
        System.err.println(polReg.RMSE());
        System.out.println(greenCode + String.format("%.8f", polReg.R2Score()) + defaultCode);
        System.out.println(greenCode + String.format("%.8f", polReg.R2ScoreVal()) + defaultCode);
        
    }
}
