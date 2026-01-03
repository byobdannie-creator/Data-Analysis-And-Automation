# The Analysis


## 1. What are the most in demand sills for the top 3 popular roles?

To find the most demanded skills foer the top 3 roles, I filtred out those positions by which I got the most popular, and got the top 5 for the top 3 roles. This highlists most popular job titles and their top skills showing which skills I should pay attention on depending on my terget role. (Python For Data Analysis)

View my notebook with details here:
[02_Skill_Demand.ipynb](03_Projects\02_Skill_Demand.ipynb)


### Visualise Data

'''python
fig, ax = plt.subplots(len(job_titles), 1)

sns.set_theme(style='ticks')

if len(job_titles) == 1:
    ax = [ax]

for i, job_title in enumerate(job_titles):
    df_plot = (
        df_skill_perc[df_skill_perc['job_title_short'] == job_title]
        .head(5)
    )

    sns.barplot(
        data=df_plot,
        x='skill_percent',
        y='job_skills',
        ax=ax[i],
        hue='skill_count',
        palette='dark:r_r'
    )

    ax[i].set_title(job_title)
    ax[i].set_xlabel('')
    ax[i].set_ylabel('')
    ax[i].get_legend().remove()
    ax[i].set_xlim(0, 78)

    for n, v in enumerate(df_plot['skill_percent']):
       ax[i].text(
        v + 1,
        n,
        f'{v:.0f}%',
        va='center',
        ha='left'
)
    if i != len(job_titles) -1:
        ax[i].set_xticks([])

fig.suptitle('Likelihood of Skills Demand in US Job Postings', fontsize=15)
fig.tight_layout(h_pad=0.5)
plt.show()
'''

##Results
![Visualisation of top skills for data roles](03_Projects\skill_demand_top3_roles.png)

# Insights

- Python is a varsatile skill and highly demanded accross top 3 roles, but most prominently for Data Scientist (72%) and Data Engineers (65%)
- SQL is the most requested skill for Data Analytics and Data Scientists with over half the job postings fot both roles. For Data Engineers, Python Is the most sought-after skill appering in 68% of job postings.
-Data Engineers requires more specialised technical skills (AWS, Azure, Spark) compared to Data Analysts and Data Scientists who are expected to be proficient in more in more general data management and analysis tools (Excel, Tableau)