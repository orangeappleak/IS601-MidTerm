# Python Calculator Midterm Project

## Project Description:

The Python Calculator Midterm Project is a modular application designed for arithmetic calculations with support for dynamic plugin system features. The application features an App class responsible for loading plugins and executing commands via a CommandHandler mechanism. It offers various arithmetic operations like addition, subtraction, division, and multiplication through its plugin system. These operations are stored as commands within the plugin folder, dynamically loaded, and registered using the CommandHandler. Additionally, the project includes a CalculationHistory class that manages calculation history, allowing users to load, save, clear, and delete historical records. Calculation records are saved in a .csv file using the pandas library. The project employs a LoggingUtility class for comprehensive logging across the application. Its modular structure facilitates scalability, enabling the addition of more complex operations or functionalities by adding new plugins.

## Configuration:

- **logging.conf**: This configuration sets up a basic logger with a console handler to configure logging. It defines the format for log messages and the date format.
- **.env**: Environment variables are managed using a .env file. Libraries like dotenv can load these variables at runtime.
- **pytest.ini**: This configuration specifies the minimum pytest version, default options when running pytest, and the directory where test files are located.

## Design Patterns Used:

- **Singleton Pattern**: The CalculationHistory class uses the singleton pattern to ensure only one instance is created. It employs the 'new' method and a private class variable '_instance' to hold the singleton instance. When a new instance is requested, the class checks if an instance already exists; if not, it creates one.
- **Command Pattern**: The CommandHandler and Command abstract class (ABC) implement the command pattern, encapsulating requests as objects and allowing parameterization of clients with queues, requests, and operations.
- **Factory Method Pattern**: The load_plugin_commands method in the App class acts as a factory method, creating Command objects without specifying the exact class of objects to be created.
- **Static Class**: The LoggingUtility class contains all static methods for logging info, warning, and error messages, which are utilized by other classes in the project. Each method is decorated with '@staticmethod'.

## Environment Variables:

The CalculationHistory class utilizes the environment variable 'HISTORY_FILE_PATH' to determine the file path for storing and reading the calculation history. The load_dotenv() function loads environment variables from a .env file into the environment. The HISTORY_FILE_PATH environment variable is used throughout the CalculationHistory class to access the calculation history file. If the variable is not set, a default value of 'calculation_history.csv' is used.

## Look Before You Leap (LBYL) and Easier to Ask for Forgiveness than Permission (EAFP):

- **Easier to Ask for Forgiveness than Permission (EAFP)**: This approach is adopted in classes like App, CommandHandler, and various command classes. Instead of checking conditions before executing commands, exceptions are handled gracefully.
- **Look Before You Leap (LBYL)**: This approach is used in the CalculationHistory class, where conditions are checked before performing actions like loading, clearing, or deleting historical records.
