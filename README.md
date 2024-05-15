; ;loop
; .MODEL SMALL         
; .STACK 100H         
; .DATA              
;     MSG DB "Numbers from 1 to 10: $"  
; .CODE                
; MAIN PROC            
;     MOV AX, @DATA   
;     MOV DS, AX      
;     MOV DX, OFFSET MSG  
;     MOV AH, 09H     
;     INT 21H         
;     MOV CX, 10      
;     MOV SI, 1       

; PRINT_LOOP:         
;     MOV AX, SI     
;     ADD AX, 30H    
;     MOV DL, AL     
;     MOV AH, 02H    
;     INT 21H        
;     INC SI         
; LOOP PRINT_LOOP    

;     MOV AH, 4CH    
;     INT 21H        
; MAIN ENDP          
; END MAIN           


;;---------------------------------------------------------------------------------------------------------------



;; ADDITION 

; .MODEL SMALL         
; .STACK 100H          
; .DATA                
;     msg1 DB 'please enter num 1: $'   
;     msg2 DB 'please enter num 2: $'   
;     result DB 'the result is: $'      
;     NEWLINE DB 13,10,'$'               
;     NUM1 DB ?                          
;     NUM2 DB ?                          
;     SUM DB ?                           
; .CODE                
; MAIN PROC            
;     MOV AX, @DATA   
;     MOV DS, AX      
    
;     MOV DX, OFFSET msg1  
;     MOV AH, 09H          
;     INT 21H              

;     MOV AH, 01H          
;     INT 21H              
;     SUB AL, 30H          
;     MOV NUM1, AL         

;     MOV DX, OFFSET msg2  
;     MOV AH, 09H          
;     INT 21H              

;     MOV AH, 01H          
;     INT 21H              
;     SUB AL, 30H          
;     MOV NUM2, AL         

;     MOV AL, NUM1         
;     ADD AL, NUM2         
;     MOV SUM, AL          

;     MOV DX, OFFSET result 
;     MOV AH, 09H          
;     INT 21H              
    
;     ADD SUM, 30H         
;     MOV DL, SUM          
;     MOV AH, 02H          
;     INT 21H              
    
;     MAIN ENDP            

;;---------------------------------------------------------------------------------------------------------------





;;EVEN OR ODD ---------------------------------------------------------------------------------------

; .MODEL SMALL         
; .DATA               
;     msg3 DB 'Enter a number: $'  
;     msg4 DB 'The number is even.$'  
;     msg5 DB 'The number is odd.$'   
; .CODE                
; MAIN PROC            
;     MOV AX, @DATA    
;     LEA DX, msg3     
;     MOV AH, 09H      
;     INT 21H          

;     MOV AH, 01H      
;     INT 21H          
;     SUB AL, 30H      

;     TEST AL, 01H     
;     JZ EVEN          

;     LEA DI, msg5     
;     JMP DISPLAY      

; EVEN:
;     LEA DI, msg4     

; DISPLAY:
;     MOV AH, 09H      
;     INT 21H          

;     MOV AH, 4CH      
;     INT 21H          

; MAIN ENDP           
; end main



;;---------------------------------------------------------------------------------------------------------------


;; HELLO WORLD PROGRAM 




; .MODEL SMALL
; .STACK 100H
; .DATA
;     MESSAGE DB 'Hello, World!', '$'
; .CODE
; MAIN PROC
;     MOV AX, @DATA
;     MOV DS, AX
;     MOV AH, 09H         
;     LEA DX, MESSAGE     
;     INT 21H             
;     MOV AH, 4CH         
;     INT 21H             
; MAIN ENDP
; END MAIN



;;---------------------------------------------------------------------------------------------------------------


;; INPUT STRING AND SRTING PRINT 

; .MODEL SMALL
; .STACK 100H
; .DATA
;     INPUT_MSG DB 'Please enter a string: $'
;     OUTPUT_MSG DB 'You entered: $'
;     MAX_LENGTH DB 100        ; Maximum length of input string
;     input_string DB 100 DUP('$')  ; Define space for input string
; .CODE
; MAIN PROC
;     MOV AX, @DATA
;     MOV DS, AX
    
;     ; Print prompt message asking for input
;     MOV AH, 09H
;     LEA DX, INPUT_MSG
;     INT 21H
    
;     ; Read input string from user
;     MOV AH, 0AH
;     MOV DX, OFFSET input_string
;     INT 21H
    
;     ; Print message showing the input string
;     MOV AH, 09H
;     LEA DX, OUTPUT_MSG
;     INT 21H
    
;     ; Print the input string
;     MOV AH, 09H
;     MOV DX, OFFSET input_string + 2  ; Skip the first two bytes of input buffer (length)
;     INT 21H
    
;     ; Terminate the program
;     MOV AH, 4CH
;     INT 21H
; MAIN ENDP
; END MAIN
