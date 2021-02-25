# Boolean Logic

Formalised by George Boole.

Watch the video of this here: [https://www.youtube.com/watch?v=y5Md132yIKM](https://www.youtube.com/watch?v=y5Md132yIKM).

# Bit

The fundamental particle of computing.

Can have one of two values: 0 or 1 (off or on / true or false).

----/ ----    OFF  0   FALSE

----------    ON   1   TRUE

# Operators

## NOT

Takes one operand.

Reverses or inverts the value of the operand.

NOT true == false
NOT false == true

Operand |  Output
--|--
FALSE | TRUE
TRUE | FALSE

Operand |  Output
--|--
0 | 1
1 | 0

## OR

Takes two operands: X and Y. Returns true if at least one of the operands is true, returns false if both operands are false.

Operand X | Operand Y | Output
-- | -- | --
FALSE | FALSE | FALSE
FALSE | TRUE | TRUE
TRUE | FALSE | TRUE
TRUE | TRUE | TRUE

Operand X | Operand Y | Output
-- | -- | --
0 | 0 | 0
0 | 1 | 1
1 | 0 | 1
1 | 1 | 1

Demonstration using an electrical circuit with two switches:

```
     _____/ ____
----|           |----- 0
    |_____/ ____|


     _____/ ____
----|           |----- 1
    |___________|

     ___________
----|           |----- 1
    |_____/ ____|

     ___________
----|           |----- 1
    |___________|  
```

It is a circuit with two switches in parallel.

# AND 

Takes two operands: X and Y. Returns true is both X and Y are true, otherwise returns false.

Operand X | Operand Y | Output
-- | -- | --
FALSE | FALSE | FALSE
FALSE | TRUE | FALSE
TRUE | FALSE | FALSE
TRUE | TRUE | TRUE

Operand X | Operand Y | Output
-- | -- | --
0 | 0 | 0
0 | 1 | 0
1 | 0 | 0
1 | 1 | 1

```
-----/ ----/ ---- 0

-----/ ---------- 0

-----------/ ---- 0

----------------- 1
```
It is a circuit with two switches in series.

## Application

### OR  

An instruction that should be executed if one or more conditions are true.

For example: turn on the kettle (jug) if it is 8am in the morning, OR a motion detector senses that I got out of bed.

`if (timeIs8am OR motionDetected) then TURN_ON_KETTLE`

### AND

An instruction should be executed if both conditions are true.

For example, only turn on the kettle when it is 8am, and the motion detector senses that I'm at home and awake.

`if (timeIs8am AND motionDetected) then TURN_ON_KETTLE`

You can chain more conditions together. For example: only turn on the kettle when it is 8am, and the motion detector senses that I'm at home and awake, and the kettle has got water in it.

`if (timeIs8am AND motionDetected AND kettleHasWater) then TURN_ON_KETTLE`

### Combination

You can combine different operators. 

For example: turn on the kettle when it's either 8am or the motion detector senses that I'm awake, and the kettle has water in it.

`if ((timeIs8am OR motionDetected) AND kettleHasWater) then TURN_ON_KETTLE`

```
    ___/ ____
---|         |-----/ ---- 0 | 1
    ---/ ----
```

### NOT 

Turn the stereo on at 8am if I'm still in bed.

`if (timeIs8am AND NOT motionDetected) then TURN_ON_STEREO`

This only works if the motion detector fires at exactly 8am. If I am at my desk and the motion detector doesn't pick me up, the stereo will turn on - which is not what I want.

```
clock:
  getTime()


motionSensor:
  triggerOnMotion(action)
  lastMotionDetected()

```

`if (timeIs8am AND motionSensor.timeSince(lastMotionDetected) > 4 HOURS AGO) then TURN_ON_STEREO`

     