---
layout: page
title: servers
---

# cs4241-17a server / front-end challenge: "API" Design and Use

In this activity, you and a team will create and document an API.
API design is an art and science, requiring you to think about how to slice and dice your data to make it usable in other applications.
This activity lets you experiment with creating, documenting, and using "APIs".

### The Twist
Your team will be designing an API that __another team__ will use to build a front-end.
Keep everyone else in the dark until it's time to "reveal".

The APIs will be built from a dataset of your choosing.
Links below will give you some pointers to find datasets and example APIs.

### The API Process
Your APIs must serve **parts** of a dataset, not the whole thing.
An example is allowing API users to filter entries on dates, by values, and providing access for individual rows based on keys.

Only read access is necessary for now, though add/update would be interesting to add if your team has bandwidth.
The simplest version of an API will read a dataset into memory, and serve up various parts of it based on query strings.
More robust versions might transform the dataset into a database (e.g. inserting the rows into SQLite or Mongo), and provide functions that execute queries based on request strings.

When forming teams, seek out folks with diverse skillsets that will help you knock this out.
Database experience is a plus, as is familiarity with manipulating tabular (csv) or JSON data (python or similar langauges are good for this).

### The Switch
Your team's API should be complete at the halfway point.

At this point, your team will split two groups: those that maintain the API while others build on it, and those who are building an application based on another team's API.

The maintenance job is straightforward: keep the server running, play tech support as crashes arise.
Any queries should be sent and addressed on Slack. 
Threads might be good for this.

The front-end team will be assigned a random API to build from.
Read your assigned API, and come up with a design that uses the application.

### The Data

I strongly suggest you choose a dataset from this site:

- https://tinyletter.com/data-is-plural/archive

A Google Spreadsheet with all entries is here:

- https://docs.google.com/spreadsheets/d/1wZhPLMCHKJvwOkP4juclhjFgqIY8fQFMemwKL2c64vk/edit#gid=0

Avoid datasets that will require significant cleanup, as you want to spend most of your time designing the API page and writing API functions.

Example APIs:

- https://dev.twitter.com/overview/api

Twitter is the closest to what you'll want for this activity.
Here are a few more (I wouldn't spend too much time perusing them, but a quick look is fine):

- https://www.instagram.com/developer/
- https://api.slack.com/
- https://developers.trello.com/

### The Finale

With 10 minutes to go, we'll cover the front-ends and API pages folks hacked together. 
Congratulations, you're now ready to create your own APIs.

