Streamlit simplifies the process of turning data scripts into shareable web apps, enabling data scientists and engineers to quickly create interactive dashboards, visualizations, and user interfaces for their projects.

Streamlit is designed to be compatible with various data visualization libraries, including Seaborn ([[streamlit-and-seaborn]]).

## How it works

Streamlit apps are [[Python]] scripts that run from top to bottom. Every time a user opens a browser tab pointing to your app, the script is re-executed. As the script executes, Streamlit draws its output live in a browser.

Each Streamlit call on the [[Python]] side loads up a React component from the running Streamlit server, which is then rendered onto your web browser. If we go under the hood of a `st.markdown` call:

![Pasted image 20230829160339.png](app://aeca1fcb7ec96b02f7f6828e45f70c4ca747/Users/lucaverhees/Obsidian/lucavh/assets/Pasted%20image%2020230829160339.png?1693317819367)

## Getting started

To get started with Streamlit, follow these steps:

1. **Installation:** Install Streamlit using pip: `pip install streamlit`
2. **Create an App:** Write a Streamlit app script using [[Python]], see an example below.

Here's a simple example of a Streamlit app that displays a line chart based on user-selected data:

```python
import streamlit as st
import pandas as pd
import matplotlib.pyplot as plt

# Load data
data = pd.read_csv("data.csv")

# Title and description
st.title("Interactive Data Visualization")
st.write("Select data to visualize:")

# User input
selected_columns = st.multiselect("Select columns", data.columns)

# Display chart
if selected_columns:
    plt.figure(figsize=(10, 6))
    for column in selected_columns:
        plt.plot(data[column], label=column)
    plt.xlabel("X-axis")
    plt.ylabel("Y-axis")
    plt.legend()
    st.pyplot(plt)
```

3. **Run the App:** In your [[terminal]], navigate to the directory containing the app script and run it using the following command: `streamlit run app_name.py` 
4. **View the App:** After running the command, Streamlit will open a new tab in your default web browser, displaying the interactive app.

## Resources
- https://docs.streamlit.io/library/cheatsheet
- https://docs.streamlit.io/

[[data-visualization]]