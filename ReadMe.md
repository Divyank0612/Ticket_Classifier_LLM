======================
TICKET CLASSIFIER LLM
======================
A Python project for support ticket classification and resolution using a local LLaMA 3 model via Ollama.
This project provides an all-in-one solution for classifying tickets and generating helpful answers interactively or from a predefined list.

------------------------------
TABLE OF CONTENTS
------------------------------
1. Features
2. Installation
3. Dataset
4. Usage
   -Manual Ticket Classification
   -Interactive LLM Assistant
5. Output Format
6. Folder Structure
7. License
8. Notes

------------------------------
1. FEATURES
------------------------------
- Classifies support tickets into categories:
  - Login/Access Issue
  - HR Query
  - IT Support
  - Other
- Generates short, helpful answers for each ticket.
- Supports manual ticket lists and interactive user input.
- Saves results to timestamped text files.
- Supports few-shot learning from a dataset for better predictions.
- Easily extendable with additional categories or prompts.

------------------------------
2. INSTALLATION
------------------------------
1. Clone this repository:
   git clone https://github.com/Divyank0612/Ticket_Classifier_LLM/

2. Install Python dependencies:
   pip install ollama pandas

3. Ensure you have the LLaMA 3 model installed locally via Ollama.

------------------------------
3. DATASET
------------------------------
A synthetic dataset (ticket.csv) with 200 tickets is included for training and few-shot examples.

- Columns: Ticket, Category
- Categories: Login/Access Issue, HR Query, IT Support, Other
- The dataset is used for few-shot examples to improve LLM performance.
- You can extend this dataset with your own tickets.

------------------------------
4. USAGE
------------------------------

a. Manual Ticket Classification

Classify a predefined list of tickets and save the results:

from ticket_assistant import classify_and_answer_tickets

manual_tickets = [
    "I forgot my password, how to reset it?",
    "I can’t log in, as password is incorrect.",
    "How to see leave balance?",
    "Laptop not turning on after update."
]

classify_and_answer_tickets(manual_tickets, username="divyank")

- Output file will be saved in classified_tickets/ as <username>_tickets_<timestamp>.txt

b. Interactive LLM Assistant

Classify tickets interactively and get answers in real-time:

from ticket_assistant import classify_and_answer_tickets

if __name__ == "__main__":
    while True:
        user_ticket = input("Enter your support ticket (or type 'exit' to quit): ")
        if user_ticket.lower() == "exit":
            break
        classify_and_answer_tickets([user_ticket], username="divyank")

- The LLM returns both Category and Answer for each ticket.
- Results are saved in classified_tickets/ with timestamped filenames.

------------------------------
5. OUTPUT FORMAT
------------------------------

All outputs follow this format:

Ticket: "<ticket text>"
Category: <predicted category>
Answer: <short, helpful solution>
---

Example:

Ticket: "I forgot my password, how to reset it?"
Category: Login/Access Issue
Answer: Please use the "Forgot Password" option on the login page. You’ll receive a reset link via email.
---

------------------------------
6. FOLDER STRUCTURE
------------------------------

Ticket_Classifier_LLM/
-classified_tickets/         
-tickets.csv  
-ticket_classifier.ipynb          
-README.md                   

------------------------------
7. LICENSE
------------------------------

This project is licensed under the MIT License.

------------------------------
8. NOTES
------------------------------

- Make sure your local LLaMA 3 model is properly installed via Ollama.
- Few-shot learning uses random samples from the dataset to improve classification.
- You can easily modify the system prompt in ticket_assistant.py to add more categories or customize answers.
