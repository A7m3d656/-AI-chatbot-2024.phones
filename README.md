# -AI-chatbot-2024.phonesimport streamlit as st
import pandas as pd

st.title("2024 Mobile Phone Specs Chatbot")

# Load phone specs data
phones = pd.read_csv("phones_2024.csv")

st.write("Ask me about any 2024 mobile phone!")

phone_name = st.text_input("Enter phone name:")

if phone_name:
    match = phones[phones['Name'].str.lower() == phone_name.lower()]
    if not match.empty:
        st.write(f"Top 10 specs for {phone_name}:")
        for col in match.columns[1:]:
            st.write(f"- {col}: {match.iloc[0][col]}")
    else:
        st.write("Sorry, I only provide info about 2024 mobile phones. Please check the name and try again.")
