# Echo-Bot

Code utilizes the Streamlit library, a popular Python framework for creating interactive web applications with minimal effort. Streamlit is known for its simplicity and ease of use, making it suitable for rapidly developing data-centric applications and interactive user interfaces. The code leverages Streamlit's features such as st.title for setting the application title, st.chat_input for capturing user input, and st.chat_message combined with st.markdown for displaying chat messages in a conversational format. The application's state management is handled through Streamlit's st.session_state, which allows for the preservation of data between different user interactions or app reruns. Overall, Streamlit is the key technology enabling the creation of a user-friendly Echo Bot interface in this code.

## Library Used: [`Streamlit`](https://docs.streamlit.io/)

Streamlit is a powerful and user-friendly Python library designed for rapidly creating interactive web applications with minimal coding effort. It simplifies the development process by providing a high-level API that allows developers to focus on building applications rather than dealing with the intricacies of web development. With its intuitive syntax and a wide range of built-in components, Streamlit is particularly well-suited for data scientists and engineers who want to quickly turn data scripts into shareable and interactive web apps. The library seamlessly integrates with popular data science tools and frameworks, making it a versatile choice for creating dashboards, visualizations, and interactive interfaces for machine learning models. Its ability to automatically handle the underlying web infrastructure, combined with real-time updates and easy deployment options, makes Streamlit an accessible and efficient solution for bringing data-driven applications to life.

## Installation Process

To install Streamlit, you can use the following command in your terminal or command prompt:

```bash
pip install streamlit
```

This command uses the Python package manager (`pip`) to download and install the Streamlit library. Make sure you have Python installed on your system before running this command.

Once the installation is complete, you can verify it by running:

```bash
streamlit --version
```

This command should display the installed Streamlit version, confirming a successful installation. After the installation, you can start building Streamlit applications using the provided Python API. To run a Streamlit app, create a Python script with your application code and execute:

```bash
streamlit run your_app.py
```

Replace `your_app.py` with the filename of your Streamlit application script. This will launch a local development server, and you can view your Streamlit app in a web browser at the provided URL (usually `http://localhost:8501`).


## How code works?

Certainly! Let's break down the code step by step:
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

![](https://i.imgur.com/bF6U3Wt.png)
