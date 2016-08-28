---
published: true
---
I'm going to switch gears a bit and post about my experience during my first week at Metis. I'll also be writing a technical analysis of my first major project (codenamed **Benson**) that was submitted in week one. I'll probably do more of a Q&A sort of post in the future that dives deeper into what a week realy feels like at Metis. But for this post, I'll keep the weekly summary brief and write more regarding Benson.

## My first week at Metis.
The day before my first class came along, and I had just completed the course's prework, which took quite some time and was fairly challenging. Looking back, the prework material really did give me a solid foundation for the class(so for those of you who are pushing it off, get to it!).

First day of class came along, and I walked into into the class with really no expectations. I heard that coding bootcamps were tough, but I had never met anyone who had completed the Metis Bootcamp before. I was pleasantly surprised when I had a chance to look at the the schedule for the first few days day. It seemed well planned and manageable if I spent my time wisely.

The day kicked off with some breakfast and introductions from the faculty members. After introductions and some "housekeeping", we were given a pair programming problem to solve. It was a pretty tough one actually, but it sparked a lot of fruitful discussions and pushed us to really think outside the box. Before I knew it, it was already lunch time.

After lunch, we were given a a turotial on how to use Git and then got got placed into our groups for our first project. At Metis, they codename each of the projects with the name of an investigator from a t.v show to follow a sort of "investigation" theme. The first one was named Benson, after a detective on Law and Order. The rest of the day was spent working on challenges (a.k.a homework) and also planning with my group.

> TL:DR : Here's what my a typical day at Metis looks like:

- 9:00 am: Good morning! ☕
- 9:15 am: Pair Programming Problem
- 10:00 am: Review Pair Programming
- 10:15 am: Break
- 10:30 am: Lecture
- 12:00 pm: Lunch
- 1:30 pm: Investigation Presentation (I'll write more about this in the future)
- 2:00 pm: Lecture
- 3:00 pm - 6:00 pm: This generally varies, but this is time usually spent working on homework (also known as challenges), group projects, or listening to speakers.

## MTA Turnstile Data Analysis

For the second half of the blog post, I wanted to introduce a concept I had learned a long time ago that may help fellow data scientists explain their project workflow coherently and succintly. It's called the S.T.A.R method, which is an acronym that stands for:

1. **S**ituation
2. **T**ask
3. **A**ction
4. **R**esult

I cannot count the number of times that I've used this method in interviews to help me describe problems that I've solved while hitting on the major points of the project.

[Read more about the S.T.A.R technique here](https://www.theguardian.com/careers/careers-blog/star-technique-competency-based-interview "Using the S.T.A.R technique to explain a problem")

**Situation:**
For the situation, we were given the link to New York's Subay [MTA Turnstile Data](http://web.mta.info/developers/turnstile.html). and pretty much free reign as to how to analyze the data and make sense of it visually.

**Task:**
My team and I reviewed the map and noticed that there was a gap between Queens and Brooklyn where the MTA Subway tracks didn't really travel (see figure 1 below). For commuters who wanted to travel between those two areas using the Subway, they would have to take a rather long roundabout way that would increase their daily commute time.

_Figure 1 : New York Subway Station Map_
<img src="{{ site.url }}{{ site.baseurl }}/images/NYC_subway-4D.svg.png" alt="">

**Action:**
We decided to create a fictional startup named Qubra that had just recently acquired shuttles and buses. This business was looking for consultants who could help maximize the potential of their recently acquired vehicles. After writing the business a  preliminary analysis (Sample page in Figure 2), we thought that it would be a good choice for the business to set up shuttles that could take commuters directly from Brooklyn to Queens (or vice versa) at the points that totaled the most foot traffic.

_Figure 2 : Sample page from the Client Report_
<img src="{{ site.url }}{{ site.baseurl }}/images/Graphs.png" alt="">

Since the data needed cleaning, I was tasked with not only munging/cleaning it but also creating the intial code that would calculate the totals of each station per day. (See code snippet in Figure 3). After completing this step, I also decided to plot some of the data to see if any patterns stood out.

From there, my teammates and I wrote additional code to handle edge cases and also worked together to plot the data using seaborn and matplotlib.

_Figure 3 : Imports we used and some code regarding the calculations._ [To view the Jupyter notebook, click here](http://nbviewer.jupyter.org/github/floofydugong/benson-five/blob/master/Benson_Team5_Analysis.ipynb# "Notebook of Team 5's Benson Project")


```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import pprint
import glob
%matplotlib inline

list_of_files = []
for filename in glob.glob("turnstile_*.txt"):
    list_of_files.append(filename)

df = pd.concat(pd.read_csv(file) for file in list_of_files)

df.columns = df.columns.str.strip()

df_entries = df.groupby(['STATION','UNIT','C/A','SCP','DATE'], as_index=False)['ENTRIES'].min()
df_entries['NEXT_DAY_ENTRIES'] = df_entries['ENTRIES']
df_entries.NEXT_DAY_ENTRIES = df_entries.NEXT_DAY_ENTRIES.shift(-1)
df_entries['ENTRY_COUNT'] = df_entries['NEXT_DAY_ENTRIES'] - df_entries['ENTRIES']
df_entries = df_entries[(df_entries.ENTRY_COUNT > 0) & (df_entries.ENTRY_COUNT < 200000)]
df_entries = df_entries.groupby(['STATION','DATE'], as_index=False)['ENTRY_COUNT'].sum()
df_entries = df_entries[df_entries.DATE != "11/06/2015"]
```
**Results:**

On Friday, we completed the finishing touches on the calculations and placed all of that into a iPython notebook for submission. We also created a powerpoint and proposal document, which we gave a presentation on to the whole class(See a sample page on Figure 4). Our final solution not only provided the client with potential stations that handled lots of foot traffic, but also specific times in which they should schedule their shuttle for pick-ups/drop-offs.

_Figure 4 : Final page taken from our proposal document_
<img src="{{ site.url }}{{ site.baseurl }}/images/results.png" alt="">

> TL:DR Overall, I was extremely pleased with the final product of my first project. My teammates were a joy to work with, and I really can't wait to start my next project!
