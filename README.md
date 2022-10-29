# MY-SQL- 
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
--FUNCTION TO CALCULATE THE SALARY FOM ANY DATE TO TODAY 
CREATE or replace FUNCTION calculate_salary(p_date date , p_empno number) 
   RETURN  NUMBER
   IS 
   p_sal NUMBER(11);
   a_1 NUMBER(11);
   a_2 NUMBER(11);
   BEGIN 
      SELECT sal , (sysdate-p_date) , (LAST_DAY(P_DATE)-TRUNC(P_DATE,'MM'))+1 
      INTO  p_sal , a_1 , a_2  
      FROM scott.emp
      WHERE p_empno=empno ;
      RETURN (round(a_1*(p_sal/a_2))); 
    END;
    
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
--TO TRYE THE FUNCTION WITH DATE AND EMPLOYYE'S NUMBER GIVEN

select calculate_salary('30-AUG-2022' , 7788 )
from scott.emp
    
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
--TO RETURN THE EMPLOYEE'S NUMBER AND SALARY

select empno , sal
from SCOTTemp

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
--FUNCTION TO CALCULATE THE SALARY FOM ANY DATE TO TODAY

CREATE or replace FUNCTION calculate_salary(p_date date , p_sal number) 
   RETURN  NUMBER
   IS 
   p_empno number(11);
   a_1 NUMBER(11);
   a_2 NUMBER(11);
   BEGIN 
      SELECT  (sysdate-p_date) , (LAST_DAY(P_DATE)-TRUNC(P_DATE,'MM'))+1 
      INTO   a_1 , a_2  
      FROM scott.emp
      where p_sal=sal;
      RETURN (round(a_1*(p_sal/a_2))); 
    END;
    
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
--TO TRYE THE FUNCTION WITH SAL AND DATE GIVIN

select calculate_salary('30-AUG-2022' , 800 )
from scott.emp
    
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
--TO RETURN THE EMPLOYEE'S NUMBER 

select empno , sal
from SCOTT.emp
