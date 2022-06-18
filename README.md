This prototype mainly focuses on slimming JavaScript by identifying and removing unused foreign functions (UFF). The prototype is developed using Node.js execution environment (>= v6.1.0). The following steps are needed for running the tool:

Install Node.js environment Install the project dependencies (npm install)

We have used a sample website which is hosted on web by using hiroku (https://aliptwebsite.herokuapp.com/)

First, we go to the path of the project(math.js) to optimize by using following 
command cd [D:\fidelity\UFFRemover-master]

After that We have instrumented the java script code of sample website using the following command 
node [D:\fidelity\UFFRemover-master] instrument_file [math.js]

This step generates a new file, math-instrumented.js .Replace original file with instrumented file To generate profiling information, We replaced sample site the original file with the instrumented file. 
For Example: Replace
 <script src="math.js"></script> 
 with
 <script src="math-instrumented.js"></script>

Next step is generating profiling info, We ran the application and used it. This step prints profiling information about used functions into the browser console. After that We saved this information, for this step, open the browser console and save the content into a txt file(profiling).

Now, We can use the registered information to optimize your application.
The optimization removes the unused foreign functions from the js file optimized. All the functions removed are listed in a folder created by the tool called "uff" in the same folder in which the optimized file is located. To avoid potential runtime errors owing to functions removed wrongly, UFFRemover replace the functions with an AJAX synchronous call that dynamically load the function from the server in case of need it.

We have optimized the original code of sample website (math.js) using following 
command node [D:\fidelity\UFFRemover-master] optimize_file_browser [math.js] [profiling.txt] 
This step generates a new file, e.g. math-optimized.js