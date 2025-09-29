# MDP REPRESENTATION

## AIM:
To represent the vacuum cleaner problem in Markov Decision Problem (MDP) form.

## PROBLEM STATEMENT:

### Problem Description
A vacuum cleaner operates in a small environment with Three adjacent cells:
Pos(P)Left (L) and Right (R). Each cell can be either Clean or Dirty. The vacuum starts in
L. The task: clean both cells (make both Clean). Design an MDP so the agent learns to
clean both cells with minimum steps.

### State Space
Available States Are: pos,Left,Right

### Sample State
We took Right as an sample State.

### Action Space
The action can be taken by the vacuum cleaner are: Suck, MoveLeft, MoveRight,
NoOp(NoOp can be used if nothing to do.)

### Sample Action
The Sample action are: Suck

### Reward Function
r(s,a,s') = +10 for cleaning a dirty cell, −1 per time-step to encourage speed, 0
otherwise. It will become terminal when both cells are Clean.

### Graphical Representation
<img width="1115" height="637" alt="image" src="https://github.com/user-attachments/assets/ca45647d-5c00-44ee-9d43-6004afc3bdcc" />

## PYTHON REPRESENTATION:
```
BY: Jeevanesh S
REG: 212222243002
```
```
P = {
    (0, 0, 0): {   # (Agent Left, Left Dirty, Right Dirty) - Start
        0: [(1.0, (0, 1, 0), +10, False)],  # Suck -> Left cleaned
        2: [(1.0, (1, 0, 0), -1, False)],   # MoveRight
        3: [(1.0, (0, 0, 0), -1, False)]    # NoOp
    },
    (0, 1, 0): {   # (Agent Left, Left Clean, Right Dirty)
        2: [(1.0, (1, 1, 0), -1, False)],   # MoveRight
        3: [(1.0, (0, 1, 0), -1, False)]    # NoOp
    },
    (1, 1, 0): {   # (Agent Right, Left Clean, Right Dirty)
        0: [(1.0, (1, 1, 1), +10, True)],   # Suck -> Both Clean → Goal
        1: [(1.0, (0, 1, 0), -1, False)],   # MoveLeft
    },
    (1, 1, 1): {   # Goal state (Both clean)
        0: [(1.0, (1, 1, 1), 0, True)],     # Any action keeps terminal
        1: [(1.0, (1, 1, 1), 0, True)],
        2: [(1.0, (1, 1, 1), 0, True)],
        3: [(1.0, (1, 1, 1), 0, True)]
    }
}

print(P)
```

## OUTPUT:
<img width="1148" height="897" alt="image" src="https://github.com/user-attachments/assets/1f0c6944-ecd4-4184-b1d5-b274acb727c5" />

## RESULT:
Thus, the vacuum cleaner problem is successfully represented in MDP form.


