# Finding-Sum-and-Difference-
Calculates sum and difference of two 8-bit unsigned numbers and sends it back into memory.
    .ORIG x3000
    
    ;Identifies 8 bit unsign and mask out bits [15:8]
    LD R5, MASK
    
    LD R0, NUM1
    LDR R1, R0, #0
    AND R1, R1, R5
    
    LD R0, NUM2
    LDR R2, R0, #0
    AND R2, R2, R5
    
    ;Add then store
    ADD R3, R1, R2
    LD R0, RLTA
    STR R3, R0, #0
    
    ;Subtract then store
    NOT R6, R2
    ADD R6, R6, #1
    ADD R4, R1, R6
    LD R0, RLTD
    STR R4, R0, #0
    
    HALT
    
NUM1    .FILL x4500
NUM2    .FILL x4501
RLTA    .FILL x4502
RLTD    .FILL x4503
MASK    .FILL x00FF

    .END
