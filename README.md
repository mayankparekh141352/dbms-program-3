# dbms-program-3

Write a PL/SQL block which displays all records of Male employees working in HR Dept from EMP table.


set serveroutput on;

declare

    cursor c_emp is select *from empwhere gender = 'male'and deptname = 'hr';

    v_emp emp%rowtype;

begin

    open c_emp;

    loop

        fetch c_emp into v_emp;
        exit when c_emp%notfound;

        dbms_output.put_line(v_emp.empno || '  '||v_emp.ename || '  ' ||v_emp.deptname || '  ' ||v_emp.gender || '  ' ||v_emp.sal);

    end loop;

    close c_emp;
end;
/

