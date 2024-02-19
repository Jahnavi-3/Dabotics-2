# Dabotics-2
Chatbot

import random

# Define responses for different types of queries
responses = {
    "greeting": ["Hello! How can I assist you today?", "Hi there! What can I help you with?"],
    "farewell": ["Goodbye! Have a great day!", "See you later!"],
    "thanks": ["You're welcome!", "Glad I could help!"],
    "default": ["I'm sorry, I didn't understand that.", "Could you please rephrase that?"],
    "knowledge": {
        "who is": "I'm sorry, I'm not an expert on specific individuals.",
        "what is your name": "I'm  siri.",
        "where is": "I'm sorry, I don't have that information.",
        "when is": "I'm sorry, I don't have that information.",
        "how to": "I'm sorry, I'm not capable of providing instructional content."
    }
}

# Function to generate responses based on user input
def generate_response(user_input):
    user_input = user_input.lower()
    if any(greeting in user_input for greeting in ["hello", "hi", "hey"]):
        return random.choice(responses["greeting"])
    elif any(farewell in user_input for farewell in ["bye", "goodbye"]):
        return random.choice(responses["farewell"])
    elif any(thanks in user_input for thanks in ["thanks", "thank you"]):
        return random.choice(responses["thanks"])
    else:
        for keyword, response in responses["knowledge"].items():
            if keyword in user_input:
                return response
        return random.choice(responses["default"])

# Main function to interact with the chatbot
def main():
    print("Chatbot: " + generate_response(""))
    while True:
        user_input = input("You: ")
        if user_input.lower() == "exit":
            print("Chatbot: " + generate_response("bye"))
            break
        response = generate_response(user_input)
        print("Chatbot: " + response)

if __name__ == "__main__":
    main()

