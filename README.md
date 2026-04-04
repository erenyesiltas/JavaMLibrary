# JavaMLibrary
This project was created to develop self-coding and statistical skills in the field of machine learning using Java. I learned statistical methods for machine learning in a course I took at university, and I wanted to improve myself by applying these fundamentals to Java. Even with artificial intelligence and standardized libraries, in a scenario where the internet and everything else were to disappear one day, having the ability to build these things from scratch is crucial.

User Guidance;

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






##Example code;

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
