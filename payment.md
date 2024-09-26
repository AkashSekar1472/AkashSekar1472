CREATE TABLE FEES (
    ROLL_NO NUMBER(20),
    NAME VARCHAR2 (50),
    total_fee NUMBER(10),
    pending_fee NUMBER(10),
    updated_status VARCHAR(30));
   

insert into FEES  values (101,'akash' , 5000, 2000 , 'PENDING');
insert into FEES values (102,'bharath',5000, 1200 , 'PENDING');
insert into FEES values (103,'balaji',5000, 0 , 'COMPLETED'); 
insert into FEES values (104,'dina',5000, 0 , 'COMPLETED');
insert into FEES values (105,'dhinesh',5000, 0 , 'COMPLETED');
insert into FEES values (106,'deva',5000, 2200 , 'PENDING');
insert into FEES values (107,'chandru',5000, 5000 , 'PENDING');
insert into FEES values (108,'gugan',5000, 5000 , 'PENDING');
insert into FEES values (109,'prem',5000, 2000 , 'PENDING');
insert into FEES values (110,'vinay',5000, 4000 , 'PENDING');
insert into FEES values (111,'veeramani',5000, 4000 , 'PENDING');
insert into FEES values (112,'vicky',5000, 900 , 'PENDING');
insert into FEES values (113,'cheran',5000, 500 , 'PENDING');
insert into FEES values (114,'rajini',5000, 1500 , 'PENDING');
insert into FEES values (115,'mani',5000, 3000 , 'PENDING');
insert into FEES values (116,'sakthiyan',5000, 4000 , 'PENDING');
insert into FEES values (117,'sharvesh',5000, 5000 , 'PENDING');
insert into FEES values (118,'venkat',5000, 5000 , 'PENDING');
INSERT INTO FEES VALUES (119, 'arun', 5000, 0 , 'COMPLETED');
INSERT INTO FEES VALUES (120, 'priya',5000, 2000 , 'PENDING');
INSERT INTO FEES VALUES (121, 'balaji', 5000, 0 , 'COMPLTED');
INSERT INTO FEES VALUES (122, 'deepa',5000, 200 , 'PENDING');
INSERT INTO FEES VALUES (123, 'rajiv', 5000, 1000 , 'PENDING');
INSERT INTO FEES VALUES (124, 'geetha', 5000, 1000 , 'PENDING');
INSERT INTO FEES VALUES (125, 'vignesh', 5000, 5000 , 'PENDING');
INSERT INTO FEES VALUES (126, 'lavanya', 5000, 5000 , 'PENDING');
INSERT INTO FEES VALUES (127, 'saravanan',5000, 5000 , 'PENDING');
INSERT INTO FEES VALUES (128, 'ramya', 5000, 2600 , 'PENDING');
INSERT INTO FEES VALUES (129, 'gokul', 5000, 3000 , 'PENDING');
INSERT INTO FEES VALUES (130, 'meena', 5000, 2800 , 'PENDING');
INSERT INTO FEES VALUES (131, 'ajith', 5000, 2500 , 'PENDING');
INSERT INTO FEES VALUES (132, 'pooja', 5000, 2900 , 'PENDING');
INSERT INTO FEES VALUES (133, 'kumar', 5000, 3000 , 'PENDING');
INSERT INTO FEES VALUES (134, 'madhan', 5000, 4000 , 'PENDING');
INSERT INTO FEES VALUES (135, 'dinesh', 5000, 1000 , 'PENDING');
INSERT INTO FEES VALUES (136, 'nandhini', 5000, 2000 , 'PENDING');
INSERT INTO FEES VALUES (137, 'mani', 5000, 5000 , 'PENDING');
INSERT INTO FEES VALUES (138, 'asha', 5000, 2000 , 'PENDING');
INSERT INTO FEES VALUES (139, 'selva',5000, 2000 , 'PENDING');
INSERT INTO FEES VALUES (140, 'sundar',5000, 2000 , 'PENDING');
INSERT INTO FEES VALUES (141, 'gayathri', 5000, 2000 , 'PENDING');
INSERT INTO FEES VALUES (142, 'aravind', 5000, 2000 , 'PENDING');
INSERT INTO FEES VALUES (143, 'vaishnavi', 5000, 2000 , 'PENDING');
INSERT INTO FEES VALUES (144, 'mahesh', 5000, 5000 , 'PENDING');
INSERT INTO FEES  VALUES (145, 'keerthi',5000, 0 , 'COMPLETED');
INSERT INTO FEES VALUES (146, 'vijay', 5000, 2000 , 'PENDING');
INSERT INTO FEES VALUES (147, 'anu', 5000, 2000 , 'PENDING');
INSERT INTO FEES VALUES (148, 'siva', 5000, 2000 , 'PENDING');

INSERT INTO FEES VALUES (149, 'ganesh', 5000, 2000 , 'PENDING');
INSERT INTO FEES VALUES (150, 'sangeetha', 5000, 2000 , 'PENDING');
INSERT INTO FEES VALUES (151, 'ashok', 5000, 2000 , 'COMPLETED');
INSERT INTO FEES VALUES (152, 'revathi', 5000, 0 , 'COMPLETED');
INSERT INTO FEES VALUES (153, 'dhanush', 5000, 2000 , 'PENDING');
INSERT INTO FEES VALUES (154, 'shivani', 5000, 2000 , 'PENDING');
INSERT INTO FEES VALUES (155, 'arjun', 5000, 2000 , 'PENDING');
INSERT INTO FEES VALUES (156, 'hema', 5000, 0 , 'COMPLETED');
INSERT INTO FEES VALUES  (157, 'karthika', 5000, 0 , 'COMPLETED');
INSERT INTO FEES VALUES (158, 'gopi', 5000, 0 , 'COMPLETED');
INSERT INTO FEES VALUES (159, 'lakshmi', 5000, 0 , 'COMPLETED');
INSERT INTO FEES VALUES (160, 'vikas', 5000, 0 , 'COMPLETED');
INSERT INTO FEES VALUES (161, 'vaibhav', 5000, 2500 , 'PENDING');
INSERT INTO FEES VALUES (162, 'divya', 5000, 2500 , 'PENDING');
INSERT INTO FEES VALUES (163, 'suresh', 5000, 1000 , 'PENDING');
INSERT INTO FEES VALUES (164, 'sindhu', 5000, 1000 , 'PENDING');
INSERT INTO FEES VALUES (165, 'balaji', 5000, 2800 , 'PENDING');
INSERT INTO FEES VALUES (166, 'radhika', 5000, 3500 , 'PENDING');
INSERT INTO FEES VALUES (167, 'kavitha', 5000, 2000 , 'PENDING');
INSERT INTO FEES VALUES (168, 'bharath', 5000, 500 , 'PENDING');

SELECT * FROM FEES;

SELECT ROLL_NO ,NAME  FROM FEES WHERE pending_fee = 0; 

SELECT ROLL_NO , NAME FROM FEES WHERE updated_status = 'PENDING';

CREATE OR REPLACE PROCEDURE PAY_FEE (
    p_ROLL_NO IN NUMBER,
    p_PAYMENT_AMOUNT IN NUMBER
) IS
    v_pending_fee NUMBER(10);
BEGIN
    -- Retrieve the current pending fee for the student
    SELECT pending_fee
    INTO v_pending_fee
    FROM FEES
    WHERE ROLL_NO = p_ROLL_NO;

    -- Check if the payment amount exceeds the pending fee
    IF p_PAYMENT_AMOUNT > v_pending_fee THEN
        RAISE_APPLICATION_ERROR(-20001, 'Payment amount exceeds the pending fee.');
    ELSE
        -- Update the pending fee and status
        UPDATE FEES
        SET pending_fee = pending_fee - p_PAYMENT_AMOUNT,
            updated_status = CASE
                                WHEN pending_fee - p_PAYMENT_AMOUNT = 0 THEN 'COMPLETED'
                                ELSE 'PENDING'
                             END
        WHERE ROLL_NO = p_ROLL_NO;
                             
        COMMIT;  -- Commit the transaction
        DBMS_OUTPUT.PUT_LINE('Payment processed successfully!');
    END IF;
    
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No student found with the given roll number.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An error occurred: ' || SQLERRM);
END;
/
BEGIN
PAY_FEE(101 ,2000);
END;
/


