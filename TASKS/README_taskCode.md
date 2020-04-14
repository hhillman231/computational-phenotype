# About the task code:
The tasks in this folder were coded by Hanna Hillman with the assistance of Jasmine Zhou, in Prof. Samuel J Gershman's Computational Cognitive Neuroscience Lab, Harvard University. <br>

For specific questions about the task code please reach out to Hanna Hillman at hhillman231@gmail.com
For specific questions aobut the parameters chosen for each task, please review the literature document.

## jsPsych
All tasks were coded using jsPsych, version 6.0.5 <br>

Citation: <br>
de Leeuw, J. R. (2015). jsPsych: A JavaScript library for creating behavioral experiments in a web browser. Behavior Research Methods, 47(1), 1-12. doi:10.3758/s13428-014-0458-y.


## Task Construction

**All tasks have the following sections**
- Quick change variables: a list of parameters that can be easily changed, such as the number of trials per block, number of blocks, etc.
- Fullscreen: puts their browser window into fullscree (RDM does not have this but has pre_rdm which asks them to do it manually, see pre_rdm task for clarification)
- Instructions: gives them task instructions
- Instruction comprehension questions: 2 multiple choice questions that are meant to ensure that they understand the instructions. If one or more of the subjects answers are incorrect, it will take them back to the beginning of the instructions. This can occur a maximum of three times (looping back to instructions) before it will proceed with practice block or experimental block (if there is no practice block, see experiment features below)
- Post-task feedback: asks the following questions after each task:
    - Did you experience any technological issues during this task? (i.e. experiment glitch, accidentally closed window, mixed up keys, etc.)
    - Did you experience any major distractions or interruptions during this task? (If yes they can write out an explanation)
    - On the following scale from 1 to 4, how engaging (attention holding) did you find this task? (1=Not at all engaging, 2=Somewhat not engaging, 3=Somewhat engaging, 4= Very engaging)
    - Is there anything else you would like us to know? (Can be a specific concern or general suggestion for improvement)
- CSV Save: saves the data as a csv on the server given the appropriate PHP scripts (see PHP scripts section)
- Database save: saves the data on a SQL database given the appropriate PHP scripts (see PHP scripts section)
- "Dashboard": Allows subjects to take a brief pause before continuing to the next task (the last tasks of each section have this commented out )

**Experiment Features**
|                       |Practice Block|Exp Blocks| Suspicion Flags                        | Bonus Pts |
|-----------------------|--------------|----------|----------------------------------------|-----------|
|Go/NoGo                | yes          | 3        | all_one <br> time_outs <br> error_rate | 32        |
|Random Dot Kinetogram  | yes          | 4        | all_one <br> time_outs <br> error_rate | 20        |
|Slot Machine/ Bandit   | yes          | tbd      | tbd                                    | 20        |
|Numerosity Comparison  | yes          | tbd      | tbd                                    | 20        |
|Lottery Ticket         | no           | tbd      | tbd                                    | 20        |
|Change Detection       | yes          | tbd      | tbd                                    | 20        |
|Intertemporal Choice   | no           | tbd      | tbd                                    | 10*       |

* 10 points is a flat rate, no bonus points are calculated based on performance due to the nature of the task being a subjective preference

## Suspicion Flags**
Suspicion flags have their own column in the data. They vary based on task (see Experiment Features table above). <br>


**Types of Suspicion flags:**
- "all_one" = subject chose the same answer for every choice in that block*
- "time_outs" = subject did not make any active choice for any of the trials in that block*
- "error_rate" = subject has a suspiciously high error rate - the parameter for this is error_rate/error_cap and is assigned in quick change variables at the top of task code
-

* in the Go/NoGo task, even though not pressing space is technically a choice option, the "all_one" flag will only trigger if they press the space bar for every square presented, if they press nothing throughout the block the "time_outs" flag will be triggered


**flags during practice block**
- If a flag is triggered during the practice block, subjects will see a notification that 'perhaps they didn't understand the task completely' and then they are sent back to the instructions. Once they have repeated the instructions (they do not have to repeat the instruction comprehension questions) they will have another practice block. If a flag is triggered again, the process will repeat. This can happen up to three times, at which point they just proceed to the experimental block.
- This repeating practice block takes up a lot of space in the task codes, starting with "no_sus" and ending with "sus_procedure" variables.



## PHP Scripts
For each HTML script run, there are two PHP scripts to save the data into CSVs and the database.

1. write_data_[task ID].php
2. database_config_[task ID].php

These have been taken from jsPsych templates. Stripped versions of them can be found in the PHPscripts folder
