# Quizzical Suspects

## Project Objective

Have you ever encountered a concept that only became clear when you tried to implement it? Fear not, for we present the solution with "Quizzical Suspects," a demo quiz application inspired by NEDUETI's entrance test. This application features proper sign-up and login functionalities, displaying previous attempt results upon login. Users can choose from different subjects, each with three difficulty levels: Easy, Medium, and Hard. Questions are randomly selected from the database, and users can attempt the quiz multiple times.

## Features

- **Signup Feature:** Allows new users to create an account with username verification from the database.
  
- **Login:** Existing users can log in, with verification from the database and error messages for incorrect entries.
  
- **Record Page:** Displays the records of users' previous attempts.

- **Subject and Difficulty Selection:** Users can choose subjects (PL, FIT) and difficulty levels (Easy, Medium, Hard).

- **Question Display:** Displays questions fetched from the database based on user choices, with a limit of 5 random questions.

- **Result Display:** Shows the result at the end of the quiz and inserts the result into the database.

- **Try Again Option:** Allows users to play the quiz again.

## Programming Language

The project is implemented in **Python**, making use of the versatile and user-friendly programming language.

## Library

The graphical user interface is developed using the **Tkinter** library, a popular choice for creating GUI applications in Python.

## Database

Data management is handled through **Microsoft Access Databases** and **SQL** for efficient storage and retrieval.

## Preview

### Quizzical Suspects GUI

#### Login Page

![Login Page](https://user-images.githubusercontent.com/98107411/193634965-6262d94d-e181-4b4d-8ff6-5d50cd690832.png)

#### Record Page

![Record Page](https://user-images.githubusercontent.com/98107411/193635034-00781005-e0b9-4bbb-80ca-4e277dbb86a6.png)

#### Quiz Home Page

![Quiz Home Page](https://user-images.githubusercontent.com/98107411/193635088-4e32af19-6676-480e-8339-31a8e89bd1a1.png)

#### Question Display

![Question Display](https://user-images.githubusercontent.com/98107411/193635117-36bd7af5-237e-43f0-be4d-6a2b2b86c33c.png)

#### Result

![Result](https://user-images.githubusercontent.com/98107411/193635157-4a50e319-b32c-43e3-b9ed-3c1c2baba911.png)

### MS Access Database

#### Example of Some MCQs Saved in Database

![MCQs in Database](https://user-images.githubusercontent.com/98107411/193636663-618cf449-04cd-40bf-8dec-d26133251b04.png)

![More MCQs in Database](https://user-images.githubusercontent.com/98107411/193636669-714a821a-c9fc-4964-a9ae-f7d25eafdfce.png)

#### User Data Table

![User Data Table](https://user-images.githubusercontent.com/98107411/193638124-586e447a-c059-4ff3-87ce-2f9629c730e8.png)

#### Record Table

![Record Table](https://user-images.githubusercontent.com/98107411/193635432-d94ed842-2482-49cd-afc4-25bb04bf37d9.png)

## Getting Started

To get started with Quizzical Suspects on your local machine:

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-username/quizzical-suspects.git
   ```

2. **Install Dependencies:**
   - Ensure you have Python installed on your machine.
   - Install required libraries using `pip install -r requirements.txt`.

3. **Set Up the Database:**
   - Create a Microsoft Access Database or use an existing one.
   - Update database configuration in the code.

4. **Run the Application:**
   - Navigate to the project directory.
   - Run the main application file.

5. **Explore the System:**
   - Use the intuitive GUI to navigate and interact with Quizzical Suspects.
   - Enjoy exploring subjects, attempting quizzes, and checking your records!

## Contributions

Contributions to the Quizzical Suspects project are welcome. If you encounter issues or have ideas for improvements, please submit a pull request or open an issue on the [GitHub repository](https://github.com/your-username/quizzical-suspects).

## License

This project is licensed under the [MIT License](LICENSE). See the [LICENSE](LICENSE) file for more details.

Feel free to explore, learn, and enjoy the Quizzical Suspects experience! 🧠✨
