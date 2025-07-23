# python-programming-task3
# AI chatbot with helo of nlp

import nltk
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.metrics.pairwise import cosine_similarity

# Download required resources
nltk.download('punkt')

# Define some sample intents
responses = {
    "greet": "Hi there! How can I help you today?",
    "goodbye": "Goodbye! Have a great day!",
    "thanks": "You're welcome!",
    "default": "Hmm... I didn't quite catch that. Could you rephrase?"
}

# Training examples
training_sentences = {
    "greet": ["hello", "hi", "hey", "good morning"],
    "goodbye": ["bye", "see you", "farewell"],
    "thanks": ["thank you", "thanks", "much appreciated"]
}

# Flatten and label the training data
corpus = []
labels = []
for intent, examples in training_sentences.items():
    corpus.extend(examples)
    labels.extend([intent] * len(examples))

# Vectorize input
vectorizer = CountVectorizer().fit(corpus)
X_train = vectorizer.transform(corpus)

def get_response(user_input):
    user_vec = vectorizer.transform([user_input])
    similarity = cosine_similarity(user_vec, X_train)
    best_match = labels[similarity.argmax()]
    return responses.get(best_match, responses["default"])

# Chat loop
while True:
    user_input = input("You: ")
    if user_input.lower() in ["exit", "quit"]:
        print("Bot:", responses["goodbye"])
        break
    print("Bot:", get_response(user_input

    #output
    <img width="787" height="228" alt="hdjfhygj'" src="https://github.com/user-attachments/assets/65445316-2698-47db-aef2-6d6c46890675" />

