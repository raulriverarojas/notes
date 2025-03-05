# Framework for system design interviews

- Real-world system design is extremely complicated. No one expects you to design a real-world system in an hour.
- System design interviews simulate real-life problem solving of an ambiguous problem where two coworkers collaborate & come up with a solution that meets their goals
- SDI are open ended, no perfect answer
- Final design less important than process
- Primary goal of interviewer is to accurately assess your abilities. They don't want an inconclusive result
- Effective SDI gives good signals that a person can collaborate, work under pressure, and ask good questions
- Good interviewers also look for red flags over-engineering in the pursuit of design perfection will cost a company; avoid over-engineering

## 4 step process for effective SDI

### 1. Understand problem & establish design scope
- Fast answers will not give you extra points
- No right answer, not trivial
- Ask questions, clarify assumptions
  - Extremely important
  - If interviewer asks you to make your own assumptions, write them down!
- Key questions to get across:
  - Specific features product wants
  - How many users, metrics
  - How fast does the company anticipate to scale
  - Tech stack @ company

### 2. Propose high level design & get buy-in
- Great idea to collaborate with interviewer during this process
- Come up with initial blueprint, ask for feedback, treat interviewer as teammate
- Draw key components on white board or paper
- Do back of envelope calculations to eval if blueprint fits scale req
- Think out loud

### 3. High level design step cont.
- Ask interviewer if back of the env calc necessary
- Go through use cases
- API endpoints & DB schema
  - In this step relics on scope of question, for "Google search" too low level, specific backend services/types ask interviewer

### 4. Design deep dive
- To do this step you already should have agreed w/ the interviewer on approach, received feedback on high lvl ideas
- Work w/ interviewer to id & prioritize components in arch
- Depending on the system most time you want to dig into details of important components
  - i.e. URL shortener → hash functionality
- Try to keep unnecessary details into a min
- Focus of details that show you can design a scalable system

## Wrap-up
- Interviewer might have follow up questions or give you freedom to discuss other points
- If interviewer asks for improvements/bottlenecks give them
- Recap here helps interviewer
- Operation issues work well here: observability & error handling & deployment

## Time allocation for each step
In a 45 min session:
- Step 1: 3-10 min
- Step 2: 10-15 min
- Step 3: 10-25 min
- Step 4: 3-5 min
