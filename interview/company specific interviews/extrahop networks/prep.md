behavioral questions + recruiter call

intro
- cs and statistics junior studying at uiuc
- Internship experiences at a startup doing backend engineering and a unicorn doing data engineering
- Also have some research experience mostly focus on doing ai/ml integration towards web platforms

why extrahop
- ExtraHop is innovating by fundamentally **reimagining how enterprises approach network security** through consolidation and advanced AI-driven analysis. For example, recently the company announced the all-in-one sensor that eliminates the need for consumers to feed different legacy security tools. [evidence](https://www.extrahop.com/news/press-releases/extrahop-disrupts-network-detection-and-response-market-with-industry-first-all-in-one-sensor)
- Also interested because the company is solving problems in the cybersecurity at a large scale. I'm also constantly solving problems, for example in my previous research experience the platform that I was building basically was nonexistent and much of the data I had to go through extensive loops to find. I believe that Extrahop's mission and values align with mine, particularly going above and beyond to satisfy the customers challenges.
- I want to work with larger clients compared to my previous startup experience in consumer-facing roles. ExtraHop offers the right balance—it's large enough to work with substantial clients but not so large that I'd lose the opportunity to face interesting challenges and solve varied problems.


**technical questions**

[[longest palindromic substring]]
[[number of connected components in an undirected graph]]
[[evaluate binary tree]]

**behavioural questions**

**Tell me about a time when you had to learn something new to deliver an important project.**

- **Situation:** Worked as a research assistant integrating graph neural networks to help transportation engineers understand infrastructure vulnerabilities because current methods are outdated and slow
- **Task:** Had to learn new libraries such as PyTorch and NetworkX and backend integration to visualize these networks and refactor them to allow frontend utilization
- **Action:** Initially, integrating PyTorch models with the Flask API kept crashing. After two weeks of documentation and tutorials, understood how to properly structure the data pipeline. Big turning point was when my PhD mentor helped me fixed the overcomplication of refactoring the code.
- **Result:** Built an analysis tool that reduced risk assessment time from like weeks to hours, piloting with 100 engineers in the fall, stronger machine learning background and integration to frontend and backend

**Tell me about a time when your team was not in agreement when faced with an important decision.**

- **Situation:** Worked as a technical director at Garuda Hacks, Indonesia's largest hackathon, organizing team was split on if we wanted in-person or online event this year.
- **Task:** Had final say on decision so needed to gather input from all team members while understanding the pros and cons, risks associated, etc.
- **Action:** Conducted 30-minute meetings with each team member to see their specific concerns, then created a comparative analysis to see if they have similar ideas. Sent out waitlist forms to see potential participants preference (65% wanted a hybrid format over the other two). Created a weighted spreadsheet to score cost, engagement and technical feasibility.
- **Result:** Made our decision, which was to create a hybrid format so first two days they could work online and then we had a day 3 finale where they presented. Hackathon ended up delivering about 2000 participants (200%) increase from previous years.


**Give me an example of a time when you didn't think you were going to meet the commitments you promised. (Deadlines, timing, etci.)**

- **Situation:** Worked as a data engineering intern at a healthcare company building out pipelines for data consumers teams (bi analysts)
- **Task:** Initially was set a task to build pipelines for three different types of data: pharmaceutical, insurance and tele-consultation. However, realized that there was a lot of learning I needed to fully understand the whole process within a 2-month time frame.
- **Action:** About a quarter of the way, sat down with my manager, realigned my values of joining the company, decided on focusing on building just 1 pipeline for pharmacy data but scalable and that could be used as a template for future interns. Talked to mentors, coworkers and even people on other teams on how to build these while being able to go through previous documentation to fully grasp the outline.
- **Result:** Automated the ETL pipeline daily aggregating over 100k+ data, help to basically make tasks less repetitive for data consumer teams and more automatic. Documented the entire process from A-Z on confluence and learned how to seek help when needed

**Tell me about a challenging problem you faced where the usual/typical approach was not going to work.**


**Tell me about a time you made a mistake that negatively impacted the team you were working with.**

- **Situation:** At a hackathon, we were building a restaurant recommendation system to help people find restaurants in Illinois based on previous preferences
- **Task:** We split off into different sections where me and my other friend worked on the collaborative and content based filtering. However, halfway through I realized I made a mistake by working on the same thing as my friend.
- **Action:** We did our next best thing, gather our models, tried to optimize and make the best model for the collaborative filtering and try to complete that part of the project right before the end. Rather than scrapping one approach entirely, we decided to leverage both of our work by comparing the performance of each method and selecting the better-performing one. I focused on optimizing the chosen collaborative-filtering model while my friend focused on user interface and data processing.
- **Result:** 


**Tell me about a time you had to make trade-offs to complete an important project.**

- **Situation:** Worked as a ml research assistant to help detect emotional tones during interview, further creating intervention strategies for young adults with disabilities
- **Task:** We were in a rush to complete the paper they needed to submit approval, so we had to make a decision fast on model architecture and validation approach
- **Action:** I decided on using the K-means clustering approach over more complex unsupervised learning prioritizing interpretability and fast implementation. Furthermore, instead of experimenting with multiple architecture I used existing implementations that the previous researchers used which was the BERT-based NLP model and just refactored alot of the code. I established a clear baseline early and optimized iteratively rather than pursuing perfect metrics from the start.
- **Result:** Successfully met the paper submission deadline that would be actionable for those working with at-risk youth. Ended up extracting a lot of behavioral patterns that provided actionable insights on how to proceed with these young adults