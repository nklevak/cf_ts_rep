This is the September 2025 pre-registered replication of the January 2025 experiment (linked here: https://github.com/nklevak/CognitiveFatigue_TaskSpecificity/tree/main/task_code/Study2_SPR_task_code).

*definitions and notes*: 
SPRs = self-paced rest periods
the rest task and spatial recall task -> based off of the dsst task and spatial recall tasks in the niv lab demos site
the digit span task -> inspired by digit span in the Poldrack lab's experiment factory
this is run with JSPsych v 7.3 and will be hosted using Proliferate

## Basic design: 

Game A and Game B are counterbalanced to be either spatial recall or digit span.
Current ordering: ABABBABAAB (5 As and 5 Bs)
- each A block = 3 epochs of game A (10 trials each) + 2 SPR periods between epochs
- same for game B
- the epochs are always separated by an SPR period

## Experiment Timing and Parameters Documentation
- **Practice Task Structure**: 4 rest task trials, 4 digit span, 4 spatial recall + instructions
- **Main Task Structure**: ABABBABAAB pattern (10 blocks, 3 epochs per block, 30 epochs in total)
- **Trials per Epoch**: 10 trials (both games)
- **SPR Periods**: Up to 20 trials (30 seconds) between epochs
- **Bonus Structure**: $1 base + up to $2 additional based on rest usage

### Task Parameters
- Digits to memorize in Digit Span: 4
- Squares to memorize in Spatial Recall (within a 4x4 grid): 4
- Rest Trial Length: 1.525 seconds
- Maximum Response Time: 4.2 seconds (both games)
- Transition Cue Duration: 3 seconds

### Main Task Trial Numbers (per epoch)
- Digit Span Trials: 10
- Spatial Recall Trials: 10
- Rest Trials: Up to 20 (self-paced)

### Detailed Task Timings
1. Digit Span Task
  - epoch in main experiment (10 trials):
    - Sequence Presentation: 1.9 seconds (4 digits × (275ms display + 200ms gap between digits))
    - Response Window: 4.2 seconds maximum
    - *total per epoch:* 61 seconds maximum (10 × (1.9s + 4.2s))
  - practice epoch (4 trials):
    - 28.4s maximum (4 x (1.9 + 4.2 + 1 (from feedback)))
2. Spatial Recall Task
  - epoch in main experiment (10 trials):
    - initial stimulus (empty grid): 100 ms
    - Sequence Presentation: 2.06 seconds (4 squares × (315ms display + 200ms gap))
    - Response Window: 4.2 seconds maximum
    - *Total per Epoch*: 62.6 seconds maximum (10 × (2.06s + 4.2s))
  - practice epoch (4 trials):
    - 29.44s maximum (4 x (0.1 + 2.06 + 4.2 + 1 (from feedback)))
3. SPR task
  - *single trial*: 1.525 seconds (1350ms display + 175ms clear screen)
  - Practice block:
    - 10.1s (4 trials x (1.525s + 1s feedback))
  - Rest of experiment:
    - *length of all rest trials together*: 915s (30 epochs * 20 rest trials * 1.525s)

## Total Time Breakdown

**Active Task Time**
1. Main Experimental Epochs
   - Spatial Recall: 939 seconds (15 epochs × 62.6s)
   - Digit Span: 915 seconds (15 epochs × 61s)
2. Practice Epochs
   - Spatial Recall: 29.44 seconds
   - Digit Span: 28.4 seconds
   - Rest Task: 10.1 seconds
3. Additional Components
- SPR trials: 915 seconds
- Transition Cues: 90 seconds (30 cues (a transition after each epoch) × 3s)
- Rest-to-Game Transitions: 8 seconds (16 transitions × 0.5s additional duration)
- Instructions/Debrief: 240 seconds

**Final Calculation**
915s (rests) +
90s (cues) +
8s (rest-to-game transitions) +
10.1s (rest practice) +
29.44s (SR practice) +
28.4s (DS practice) +
939s (SR epochs) +
915s (DS epochs) +
240s (instructions)
= 3174.94 seconds
= 52.92 minutes
(in case instructions/survey take a long time, round up to 56 minutes)

## Bonus Structure
- Base Bonus: $1
- Additional Bonus: Up to $2
  - Calculated as: (unused rest trials / 600) × $2
- Endowment: 600 points (1 rest trial used = -1 points)

## Data Analysis Notes
For spatial recall, rest, and digit span:
- The timed_out value = 0 when it hasn't timed out and 1 if it has
- When this happens, the rt is set to the max response time (4200ms)
  - Make sure to filter out whenever timed_out = 1

- For rest when time out happens the rt is null
  - Timeout for rest is always 1 for last row when they selected to end rest
  - Real time out: rt == null AND timeout = 1