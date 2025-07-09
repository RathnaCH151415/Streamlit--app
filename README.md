import streamlit as st
import openai

st.set_page_config(page_title="Rathna's AI Chat 🤖")

st.title("🤖 Rathna's ChatGPT App")
st.write("Ask me anything!")

openai.api_key = "sk-xxxxxxxxxxxxxxxxxxxxxxxxx"  # 👉 Paste your real API key here

user_input = st.text_input("You:")

if user_input:
    with st.spinner("ChatGPT typing..."):
        response = openai.ChatCompletion.create(
            model="gpt-3.5-turbo",
            messages=[
                {"role": "system", "content": "You are a helpful assistant."},
                {"role": "user", "content": user_input}
            ]
        )
        message = response['choices'][0]['message']['content']
        st.write("🤖 ChatGPT:", message)
