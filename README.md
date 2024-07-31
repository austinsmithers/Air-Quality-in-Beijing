# Air-Quality-in-Beijing

---

### Project Overview

The goal of this project was to practice my Python skills by exploring correlations between variables effecting air pollution in Beijing, China. The data set consists of reported temperatures, dew points, pressure, wind direction/speed, snow/rain levels, and PM2.5 concentration levels (ug/m^3) at various times between 2010 - 2014. PM2.5 is a type of air pollution maade up of very fine particles that can be harmful to human health and the environment. I was interested in learning about how these variables in the environment affected PM2.5 concentration and if the variables in the environment were correlated themselves.

### Data Sources

The primary dataset used for this analysis is "data.csv" from Kaggle.com containing detailed information on weather and environmental factors in Beijing, China between 2010 - 2014.

### Tools

- Python - Data Analysis

### Data Cleaning/Preparation
In the initial data preparation phase, I performed the following:
1. Loaded the data and inspected it.
2. Checked for missing data.
3. Order data by "year"
4. Removed duplicate rows.

### Exploratory Data Analysis

My EDA involved exploring the data to answer key questions:

- How are temperature, presure, and dew point related?
- What variables are correlated to air pollution in Beijing, and how are they correlated?

### Data Analysis

The following code generates a scatter plot illustrating the relationship between temperature and pressure, with a blue linear regression line overlaid. There is a negative correlation here.

```python
sns.regplot(x="TEMP", y="PRES", data=df, scatter_kws={"color": "red"}, line_kws={"color":"blue"})
```

The following code generates a heat map that provides the correlation direction and strength across all variables in the data set. I converted "combined wind direction" from object type to numerical categories in order to include it in the heat map.

```python
df_numerized = df
for col_name in df_numerized.columns:
    if(df_numerized[col_name].dtype == 'object'):
        df_numerized[col_name] = df_numerized[col_name].astype('category')
        df_numerized[col_name] = df_numerized[col_name].cat.codes
correlation_matrix = df_numerized.corr()
sns.heatmap(correlation_matrix, annot=True)

plt.title("Correlation Matrix")
plt.xlabel("Air Quality Factors")
plt.ylabel("Air Quality Factors")
plt.show()
```

### Results/Findings

The analysis results are summarized as follows:
1. Temperature, pressure and dew point are all strongly and linearly related. As temperature and dew point increase, pressure decreases.
2. The relationships of environmental factors with air pollution, measured as PM2.5 concentration, appear to be strong, non-linear relationships. They do not have strong correlations on the heat map, because they are not linearly correlated.

### Implications/Recommendations:

If this project were for the purpose of reducing pollution in Beijing, I would continue my analysis by further exploring the strong, non-linear relationships associated with PM2.5 concentration. The goal would be to determine what factor(s) most impact PM2.5 levels and then figure out how to indirectly influence these variables (via legislation, systemic change, etc.) to decrease PM2.5 levels. Determining how to influence the variables that influence PM2.5 concentration would require further analysis on these variables.

### Limitations

There were a few limitations within this data set. One limitation was that it dates back 10 years. It would be beneficial to see more recent data on these relationships.

### References

1. [Kaggle.com](https://data.gov/](https://www.kaggle.com/datasets/stealthtechnologies/preeeeeeee)
