# Company-Manager
Capstone project for Udemy Course Python 3.

'''Company management device program'''
class Employee:
    '''abstract base class '''
    payroll_tax = 0.39    
    def __init__(self, name):
        self.name = name    
    def calc_pay(self):
        '''public method to be implemented in subclasses'''
        raise NotImplementedError("Subclass must implement abstract method")       
class Hourly(Employee):
    '''hourly payed employee object'''
    def __init__(self):        
        self.name = input("Applicant for function on hourly-based pay-rate. \nName: ")
        self.age = input("Age: ")
        self.adress = input("Adress: ")    
    def __str__(self):
        return f"Status Report for hourly employee: \nName: {self.name} \nAge: {self.age}\
        \nAdress: {self.adress}"
    def calc_pay(self):
        '''calculate monthly wages'''
        self.hour_total = int(input(f"Total amount of labour-time for Mr. / Mrs. {self.name}: "))
        self.hour_pay = int(input("Hourly rate: "))
        gross_wages = self.hour_pay * self.hour_total
        subtract = gross_wages * self.payroll_tax
        net_wages = gross_wages - subtract
        print(f"Gross wages: {gross_wages} \nwithheld: {subtract: 10.2f} \nNet wages:\
            {net_wages:10.2f}")
class Salaried(Employee):
    '''Salaried employee object'''
    def __init__(self):
        self.name = input("Applicant for function as salaried employee. \nName ")
        self.age = input("Age: ")
        self.adress = input("Adress: ")
    def __str__(self):
        return f"Status report for salaried employee: \nName {self.name} \nAge {self.age}\
        \nAdress: {self.adress}"
    def calc_pay(self):
        '''calculate monthly wages'''
        gross_wages = int(input(f'Gross wage figure for employee {self.name}: '))
        subtract = gross_wages * self.payroll_tax
        net_wages = gross_wages - subtract
        print(f"Gross wages: {gross_wages} \nwithheld: {subtract} \nNet wages: {net_wages: 10.2f}")
class Manager(Employee):
    '''manager employee object'''
    def __init__(self):
        self.name = input("Applicant for manager function. \nName ")
        self.age = input("Age: ")
        self.adress = input("Adress: ")
    def __str__(self):
        return f"Status report for manager-rank employee: \nName: {self.name} \nAge: {self.age}\
        \nAdress: {self.adress}"
    def calc_pay(self):
        '''calculate monthly wages'''
        bonus = int(input('Bonus addition figure: '))
        gross_wages = int(input(f'Gross wage for employee {self.name}: ')) + bonus
        subtract = gross_wages * self.payroll_tax
        net_wages = gross_wages - subtract
        print(f"Gross wages: {gross_wages} \nBonus: {bonus} \nwithheld: {subtract: 10.2f}\
            \nNet wages: {net_wages: 10.2f}")
class Executive(Employee):
    '''executive member object'''
    def __init__(self):
        self.name = input("Executive staff member. \nName ")
        self.age = input("Age: ")
        self.adress = input("Adress: ")
    def __str__(self):
        return f"Status report for executive member employee: \nName: {self.name} \nAge: {self.age}\
        \nAdress: {self.adress}"
    def calc_pay(self):
        '''calculate monthly wages'''
        bonus = int(input('Bonus addition figure: '))
        corporate_share = int(input('Monthly corporate share revenue figure: '))
        gross_wages = int(input(f'Gross wage for employee {self.name}: ')) + bonus + corporate_share
        subtract = gross_wages * self.payroll_tax
        net_wages = gross_wages - subtract
        print(f"Gross wages: {gross_wages} \nBonus: {bonus} \nCorporate Share figure: {corporate_share}\
            \nwithheld: {subtract: 10.2f} \nNet wages: {net_wages: 10.2f}")
class Company:
    '''Company object. Will manage Employee subclasses'''
    def __init__(self, name):
        self.name = name
    def __str__(self):
        return f"{self.name!r} Company Management Device"
    def hire_proc(self, name):
        '''hire procedure'''
        interview_score = int(input(f'Evaluation of interview with Mr./Mrs {name.name}\
        (enter score ranging 1-5): '))
        if interview_score >= 4:
            print(f"{name.name} is hired.")
            return True
        else:
            print(f"Mr/Mrs {name.name}'s application was not withheld.")
            return False
    def evaluate_employee(self, name):
        '''evaluation tool for hiring , firing and promoting'''
        evaluation = int(input('Enter evaluation score ranging from 0 - 5: '))
        if evaluation == 5:
            print(f"Employee{name.name} is raised")
        elif evaluation >= 3:
            print(f"Employee {name.name}'s status remains unchanged")
        else:
            print(f"Evaluation of interview with:- Mr/Mrs {name.name} -was unsatisfying. DISMISSED.")
            self.hire_proc = False
comp = Company("EVIL CORP. ")
print(comp)
print("\n")
x = Hourly()
print(x)
if comp.hire_proc(x):
    payday = input("Engage payment procedure? y/n: ")
    if payday[0].lower() == "y":
        x.calc_pay()
    comp.evaluate_employee(x)
print("\n")
y = Salaried()
print(y)
if comp.hire_proc(y):
    payday = input("Engage payment procedure? y/n: ")
    if payday[0].lower() == "y":
        y.calc_pay()
    comp.evaluate_employee(y)
print("\n")
z = Manager()
print(z)
if comp.hire_proc(z):
    payday = input("Engage payment procedure? y/n: ")
    if payday[0].lower() == "y":
        z.calc_pay()
    comp.evaluate_employee(z)
print("\n")
alfa = Executive()
print(alfa)
alfa.calc_pay()

