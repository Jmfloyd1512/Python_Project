# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles?

To determine which skills are most in-demand for the top three data roles. I obtained the top 5 abilities for these top 3 roles by sorting the positions based on popularity. Depending on the role I'm considering, this query reveals the most popular job titles and their top competencies, indicating which skills I should focus on.

See my notebook with all the instructions here: [2_skill_demand.ipynb]()

### Visualize Data
```python 
fig, ax = plt.subplots(len(job_titles),1)

for i, job_title in enumerate(job_titles):
    df_plot = df_skill_perc[df_skill_perc['job_title_short'] == job_title].head(5)
    sns.barplot(data= df_plot, x ='skill_percent', y = 'job_skills', ax =ax[i],  hue= 'skill_count', palette= 'dark:b_r')
    ax[i].set_title(job_title)
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].legend().set_visible(False)
    ax[i].set_xlim(0,78)
   
    for n , v in enumerate(df_plot['skill_percent']):
        ax[i].text(v+1, n, f'{v:.0f}%', va='center')
    if i !=len(job_titles) -1: 
       ax[i].set_xticks([])

fig.suptitle('Likelihood of skills required for  Job Postings in US', fontsize = 15)
fig.tight_layout(h_pad=0.5)
```
### Results
![Visualization of Top Skills for Data Nerds](3_Project\Image\Skill_demand_Final_Result.png)

### Insights
- With SQL being mentioned in more than half of job listings for both professions, it is the most sought-after ability for Data Scientists and Analysts. Python is the most sought-after talent for Data Engineers, showing up in 68% of job posts.

- Compared to Data analysts and Scientists, who are required to be skilled in more broad data management and analysis tools (Excel, Tableau), Data Engineers need more specialised technological capabilities (AWS, Azure, Spark).

- Across all three roles, but especially for Data Scientists (72%) and Data Engineers (65%), Python is a highly sought-after talent.

## 2.How are in-demand skills trending for Data Analysts?

I searched job posts for data analysts and grouped the talents according to the month in order to determine the abilities that are in demand for data analysts in 2023. I was able to obtain the top 5 data analyst skills by month, demonstrating the popularity of these skills in 2023.

See my notebook with step-by-step instructions here:[3_Skills_trend.ipynb]

### Visualize Data
```python

sns.lineplot(data=df_plot,dashes=False, palette='tab10')
sns.set_theme(style = 'ticks')
sns.despine()

from matplotlib.ticker import PercentFormatter

ax =plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals =0))

plt.title = ('Trending Top Skills fo Data Analysts in the US')
plt.ylabel('Likelihood of Job Posting')
plt.xlabel('2023')
plt.legend().remove()

for i in range(5):
    plt.text(11.2, df_plot.iloc[-1,i], df_plot.columns[i])

```

### Results
![Trending Top Skills fo Data Analysts in the US](C:\Users\Joy\Python_data_project\3_Project\Image\Skill_Trend.png)
