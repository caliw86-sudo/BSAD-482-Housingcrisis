import streamlit as st
import pandas as pd
import matplotlib.pyplot as plt

st.title("North Vancouver Housing Dashboard")

# Load your dataset
df = pd.read_csv("data/combined_data.csv")

# Sidebar filter
st.sidebar.header("Filter by Year")

year_range = st.sidebar.slider(
    "Select Year Range",
    int(df["Year"].min()),
    int(df["Year"].max()),
    (int(df["Year"].min()), int(df["Year"].max()))
)

df = df[(df["Year"] >= year_range[0]) & (df["Year"] <= year_range[1])]

# Population chart
st.subheader("Population Growth Over Time")
fig, ax = plt.subplots()
ax.plot(df["Year"], df["Population"])
ax.set_xlabel("Year")
ax.set_ylabel("Population")
st.pyplot(fig)

# Supply chart
st.subheader("Housing Supply Over Time")
fig, ax = plt.subplots()
ax.plot(df["Year"], df["Cumulative_Supply"])
ax.set_xlabel("Year")
ax.set_ylabel("Total Housing Supply")
st.pyplot(fig)

# Rent chart
st.subheader("Average Rent Over Time")
fig, ax = plt.subplots()
ax.plot(df["Year"], df["Avg_Rent"])
ax.set_xlabel("Year")
ax.set_ylabel("Average Rent ($)")
st.pyplot(fig)
