Kanban is a workflow management method that helps teams visualize work, limit work in progress, and improve how tasks move from start to finish. 

By making work visible and manageable, Kanban gives teams a clearer way to prioritize, collaborate, and deliver value more consistently.
### Key Takeaways

- Kanban is a visual [[Agile]] framework that keeps work in progress (WIP) manageable and promotes continuous improvement through transparent workflows.
- Teams use Kanban boards and cards to track tasks, identify bottlenecks, and optimize delivery cycles.
- Key practices include setting WIP limits, standardizing workflows, and using metrics like cycle time and cumulative flow diagrams.
- Teams use WIP limits on Kanban boards to stay focused, manage capacity, and keep work flowing.

Taken from https://www.atlassian.com/agile/kanban/

### Visualize the workflow

The team uses a **Kanban board** to track work.
Each task on the board is represented by a card that moves from left to right.

Example:

| Backlog | Ready  | In Progress | Code Review | Testing | Done   |
| ------- | ------ | ----------- | ----------- | ------- | ------ |
| Task A  | Task B | Task C      | Task D      | Task E  | Task F |
| Task G  |        | Task H      |             | Task I  |        |
|         |        |             |             | Task J  |        |
At any moment, everyone knows:

- What is currently being worked on
- What is blocked
- What has been completed
- Where bottlenecks exist

### Limit Work in Progress (WIP)

Limiting WIP prevents starting too much work at once and creating bottlenecks.

When a developer finishes an owned task/s, he will not immediately start the next task, instead he will 

- Review the code
- Fix any outstanding bugs
- Help testers to test the new code
- Pair program with other developers in his team.

A group of developers can finish a great deal of features and bugs and move a lot of work to QA which can cause a bottleneck. Instead, developers help with testing, review eachothers code, do backlog assignments to ease up testers.

### Pull Instead of Push

The developer doesn't get assigned new tasks (push) all the time, some tasks are backlogged, developers can take up (pull) new tasks when they can handle them.

This approach helps naturally balance workflow.

### Manage Flow

The goal isn't keeping developers busy.
The goal of developments cycles is keeping work moving smoothly.

Metrics include:

### Lead Time

Time from customer request until delivery.
Customer requests feature -> it takes 10 days to go from meeting customer to delivery -> Lead time is 10 days. 
### Cycle Time

Time spent actively working.
Development starts on Monday -> Finished at Friday -> 5 days
### Throughput

Number of completed tasks per week.

## Continuous Delivery

Kanban doesn't do traditional sprints, when a feature is done it is delivered.
Companies like Amazon, Google, and Netflix often deploy many times per day using continuous delivery practices that align with Kanban principles.

## Continuous Improvement

Kanban teams constantly examine their process.

Questions include:

- Where are the bottlenecks ? Is something stopping development and where ?
- Which column in the Kanban board keeps filling up?
- Which tasks take longest?
- Why are tasks blocked?

Then measures can be taken to improve the workflow.

## When Kanban Works Best

Kanban is particularly effective when:

- Work arrives unpredictably (support tickets, bug fixes, operational tasks).
- Priorities change frequently.
- You want continuous delivery rather than scheduled sprint releases.
- Teams maintain software after its initial release.
- You want to optimize workflow and reduce bottlenecks.

Scrum is often a better fit when work can be planned into regular iterations with well-defined goals.

## Advantages

- Easy to adopt with minimal process changes.
- High transparency into work status.
- Encourages focus through WIP limits.
- Reduces context switching.
- Reveals bottlenecks quickly.
- Supports frequent releases.
- Adapts easily to changing priorities.

## Disadvantages

- Provides less structure than Scrum, which can be challenging for new Agile teams.
- Without discipline, priorities can change too frequently.
- Estimating long-term delivery dates may be harder if work varies significantly in size.
- Teams must actively monitor and improve their workflow to gain the full benefits.

In practice, many organizations combine the two approaches in a **Scrumban** model: they use Scrum's planning and review ceremonies while managing day-to-day work with a Kanban board and WIP limits.