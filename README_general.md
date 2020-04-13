# Overview

This is a repository for the tasks and data analysis used in the computational phenotype study.


## Study Structure

This study had participants perform seven tasks, broken up into three sessions, every week for 12 weeks.
Tasks were broken up such that each session took approximately the same amount of time.
Sessions were completed once a day for three consecutive days. <br>

Prior to doing the tasks for each session, subjects completed an intro questionnaire.
This questionnaire was the same for every session with the exception of the very first session,
which is slightly longer to collect demographic information.
Furthermore, during the first week only, subjects completed two extra surveys: DOSPERT and Barratt Impulsiveness.

Over the course of the weeks, each session contained the same tasks, but the order changed (i.e. Session 1 **always** included Go/No-Go and a Random Dot Kinetogram, but the order of which came first or second was switched every week).

## Tasks

All tasks were designed using jsPsych by Hanna Hillman and Jasmine Zhou.
Custom plug-ins were designed for the change detection task, numerosity comparison task.
Custom/modified css scripts were used for the slot-machine/bandit task, change detections task, and numerosity comparison task.

A list of the tasks (and their respective sessions) is as follows:<br>
Go/NoGo - Session 1<br>
Random Dot Kinetogram - Session 1<br>
Slot Machine/ Bandit - Session 2<br>
Numerosity Comparison - Session 2<br>
Lottery Ticket - Session 2<br>
Change Detection - Sesssion 3<br>
Intertemporal Choice - Session 3<br>


## Data

Data was saved on our website server, as well as on a database managed by our website server.
To facilitate this there were 2 php scripts for each task/survey. These follow the templates provided on [jsPsych.com](https://www.jspsych.org/overview/data/#storing-data-permanently-in-a-mysql-database).
