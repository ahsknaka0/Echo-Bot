# Echo-Bot

Code utilizes the Streamlit library, a popular Python framework for creating interactive web applications with minimal effort. Streamlit is known for its simplicity and ease of use, making it suitable for rapidly developing data-centric applications and interactive user interfaces. The code leverages Streamlit's features such as st.title for setting the application title, st.chat_input for capturing user input, and st.chat_message combined with st.markdown for displaying chat messages in a conversational format. The application's state management is handled through Streamlit's st.session_state, which allows for the preservation of data between different user interactions or app reruns. Overall, Streamlit is the key technology enabling the creation of a user-friendly Echo Bot interface in this code.

```python
import streamlit as st
```
This line imports the Streamlit library and assigns it the alias `st`.

```python
st.title("Echo Bot")
```
This line sets the title of the Streamlit app to "Echo Bot".

```python
if "messages" not in st.session_state:
    st.session_state.messages = []
```
Here, it checks if the `messages` key is present in the `st.session_state`. If not, it initializes an empty list for storing chat messages.

```python
for message in st.session_state.messages:
    with st.chat_message(message["role"]):
        st.markdown(message["content"])
```
This loop iterates through the chat messages stored in the session state and displays them using Streamlit's `st.chat_message` and `st.markdown` functions. It organizes messages based on their "role" (either "user" or "assistant").

```python
if prompt := st.chat_input("What's Up?"):
    # User input handling
```
This line uses the `st.chat_input` function to get user input. If the user enters a non-empty input, it proceeds to the block of code below.

```python
    with st.chat_message("user"):
        st.markdown(prompt)
```
This section displays the user's input as a chat message.

```python
    st.session_state.messages.append({"role": "user", "content": prompt})
    response = f"Echo: {prompt}"
```
It adds the user's message to the chat history in the session state and creates a response by echoing the user's input.

```python
    with st.chat_message("assistant"):
        st.markdown(response)
```
This section displays the assistant's response.

```python
    st.session_state.messages.append({"role": "assistant", "content": response})
```
It adds the assistant's response to the chat history in the session state.

In summary, this code creates a simple Streamlit app for an Echo Bot. It allows users to input messages, echoes their input, and displays the conversation in a chat-like interface. The chat history is stored in the session state to persist messages across app reruns.
