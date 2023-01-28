autonomous - a system that can act independently, from its time of deployment

an autonomous system must have
- sensors to gather information
- processors to process info and **make decisions**
- control systems to execute commands correctly

# Technical Definitions
Concise - One sentence.
Term, Category, Distinguisihing features.

Technical descriptions can describe objects, mechanisms, and processes:
- Mecahnisms are synthetic objects consisting of multiple parts that work together as a **system**.
- Processes take place over time.

# Technical Descriptions
## Introduction
Clearly introduce the description - is it general or to a speicfic model/process?

When describing a mechanism, describe
- what is an item
- what the function of it is
- what it looks like
- how it works
- its **principal** parts (not everything)

When describing a process, describe
- what is the process
- what is the function
- where/when
- who
- how
- principal steps

## Structure
You can base your description on the steps of how an object works or is used (functional), or the physical structure of the object/mechanism (spatial). For example, in the former you would describe a car by how it starts combusting to how the engine gives power. In the latter, you would describe the casing of the car before the seats then the steering etc.

For processes, use **present tense** and describe the step-by-step description and explain the relationship between steps. Use past tense only if the process no longer occurs.

Conclusion: summarize how the parts work together and how the steps work together.

Magnetometer measures the magnetic field allows us to get an absolute xyz but is easily preturbed by local environment. this is also too slow for quadcopter control

Arduino's `pinMode()` function has the parameters `pin, mode` and configures whether the specified `pin` will be used for input or output on the board. Thus, the three possible values for `mode` are `INPUT`, `OUTPUT`, and `INPUT_PULLUP`. The last of which is technical and inverts input.

`digitalWrite()` has the parameters, `pin, value` and configures whether the specified `pin` will have a `HIGH` or `LOW` value. If the `pin` was set to output using `pinMode()`, then setting `digitalWrite()` to `HIGH` will generate a higher electrical output. Specifically, this will be 5V (or 3.3V for 3.3V boards) on `HIGH` and 0V on `LOW`. If the pin is set to `INPUT`, using `digitalWrite` to set the pin to `HIGH` will enable the internal pullup.

# Emails
SMART
![[Pasted image 20221012183518.png]]

# Visual Aids
Tables and figures are seperately numbered and named. Figures are anything that's not a table. Tables titles go above table, figure titles go below figure.

Paragraphing ideas
- forcus on one idea
- clear topic sentence
- connect ideas with transitions
- supporting details connected only to main idea
# Oral Presentations
# Structure as a Whole
### Introduction
give exactly what the presentation is about
team members + name
date
### Context/Problem
Introduce the problem you are trying to solve
### Overview + evaluation of existing solutions
Point out weak spots in existing solutions
### overview of solution and objectives
show what you can fill in and your overall goals in the objects
### Technical Requirements needed to achieve goal
### Validation plan
Testing and how to see that you've achieved your goals and your requirements
### Closing
Thank for the time, leave last slide for contact info

# Structure of a Slide
Body slide title - deliver main idea
- Bullet points in body should be short complete ideas
- bullet points optional
- anticipate audience questions
- 7 words or less
- add supporting details to main idea
### Visual Supports
- use right tool for the job
- label parts in a system
- label points to draw emphasis
- do not use figure/table titles
- avoid visual clutter
- keep labels in whitespace
### Components in Good Slide Design
- backgrounds should not compete with content
![[Pasted image 20221007211100.png]]
- choose colors to set tone, give contrast, provide emphasis
	- in graphs useful to draw attention to current year, issue, most important
- don't use walls of text
- use sans serif, whitespace
- excessive images also create visual clutter
- **only** use more than one graph in a slide if you are comparing them
# Teamwork
A team contract is an opportunity for your team to reach a consensus on overarching goals and anticipate conflicts/plan for handling them.

In a healthy team context, conflict can be good. Generate new ideas, raise questions, build better relationships
![[Pasted image 20221007213758.png]]
# Review
definition vs description, def is 1 sentence and has
- term,
- category
- distinguishing features
Appeals:
- ethos
	- credibility
- pathos
	- emotion
- logos
	- logic
- kairos
	- time and place
Slide design:
- background
- color
- text
- images
Citations:
- rare to use direct quotes in tech reports
- plagiarism is bad
# Final Project
Research a **problem** where an autonomous drone is the **best solution**. This means that the autonomy offers an advantage over a human operator.