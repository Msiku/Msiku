- 👋 Hi, I’m @Msiku
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
- 😎 
<!---

Msiku<map>

<string name="biz_block_reasons_language">en</string>

<int name="biz_block_reasons_version" value="6"/>

<string name="biz_block_reasons_country">IN</string>

<int name="biz_block_reasons_api_back_off_days" value="0"/>

<string name="biz_block_reasons">{"no_longer_needed":"No longer needed","no_sign_up":"Didn't sign up","spam":"Spam","offensive_messages":"Offensive messages","other":"Other"}</string>

<long name="biz_block_reasons_api_cooling_timestamp" value="0"/></map>

 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import matplotlib.pyplot as plt
import pandas as pd

# Data for Double Mass Analysis
data_double_mass = {
    'Year': [1971, 1972, 1973, 1974, 1975, 1976, 1977, 1978, 1979, 1980, 
             1981, 1982, 1983, 1984, 1985, 1986, 1987, 1988, 1989, 1990, 
             1991, 1992, 1993, 1994, 1995, 1996, 1997, 1998, 1999, 2000],
    'Gauge_X': [700, 550, 480, 810, 430, 910, 440, 890, 470, 300, 
                420, 430, 350, 330, 880, 640, 720, 510, 880, 590, 
                710, 560, 770, 780, 770, 790, 680, 340, 590, 340],
    'Other_Gauge_Avg': [510, 520, 490, 620, 640, 610, 550, 1110, 680, 640, 
                        620, 770, 800, 710, 730, 620, 360, 690, 600, 580, 
                        470, 720, 640, 660, 540, 850, 630, 330, 510, 340]
}

# Create a DataFrame
df_double_mass = pd.DataFrame(data_double_mass)

# Calculate Cumulative Sums
df_double_mass['Cumulative_Sum_Gauge_X'] = df_double_mass['Gauge_X'].cumsum()
df_double_mass['Cumulative_Sum_Other_Gauge'] = df_double_mass['Other_Gauge_Avg'].cumsum()

# Plot Double Mass Curve
plt.figure(figsize=(10, 6))
plt.plot(df_double_mass['Cumulative_Sum_Other_Gauge'], df_double_mass['Cumulative_Sum_Gauge_X'], marker='o', linestyle='-')
plt.title('Double Mass Curve')
plt.xlabel('Cumulative Sum of Other Gauge Average (mm)')
plt.ylabel('Cumulative Sum of Gauge X (mm)')
plt.grid(True)
plt.show()

# Data for Hyetograph and Maximum-Intensity-Duration Curve
data_rainfall = {
    'Time_hr': [22.00, 22.05, 22.10, 22.15, 22.20, 22.25, 22.30, 22.35, 22.40, 22.45, 22.50],
    'Depth_mm': [0, 10.2, 20.8, 33.0, 47.2, 55.8, 64.0, 77.6, 78.8, 85.4, 91.4]
}

# Create a DataFrame
df_rainfall = pd.DataFrame(data_rainfall)

# Calculate Incremental Rainfall
df_rainfall['Incremental_Rainfall_mm'] = df_rainfall['Depth_mm'].diff().fillna(0)

# Calculate Intensity (mm/hr)
time_interval_hr = 5 / 60  # 5 minutes in hours
df_rainfall['Intensity_mm_hr'] = df_rainfall['Incremental_Rainfall_mm'] / time_interval_hr

# Plot Hyetograph
plt.figure(figsize=(10, 6))
plt.bar(df_rainfall['Time_hr'], df_rainfall['Incremental_Rainfall_mm'], width=0.04)
plt.title('Hyetograph')
plt.xlabel('Time (hr)')
plt.ylabel('Incremental Rainfall (mm)')
plt.grid(True)
plt.show()

# Plot Maximum-Intensity-Duration Curve
plt.figure(figsize=(10, 6))
plt.plot(df_rainfall['Time_hr'], df_rainfall['Intensity_mm_hr'], marker='o', linestyle='-')
plt.title('Maximum-Intensity-Duration Curve')
plt.xlabel('Time (hr)')
plt.ylabel('Intensity (mm/hr)')
plt.grid(True)
plt.show()
