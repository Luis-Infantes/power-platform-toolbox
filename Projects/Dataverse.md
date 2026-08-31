# EJEMPLOS DE LA ESTRUCTURA DE BASE DE DATOS PARA PROYECTOS EMPRESARIALES

## 1) - GESTION DE INCIDENCIAS

### ENUNCIADO:

Una empresa de soporte IT quiere gestionar las incidencias reportadas por los empleados.
Cuando un empleado detecta un problema, registra una incidencia.
Las incidencias pueden clasificarse según diferentes categorías definidas por la empresa.
La empresa también quiere conocer qué técnico está trabajando en cada incidencia y disponer de un historial de cambios de estado.


###  TABLAS:

It_DepartamentEmployees

DepartamentEmployeesCode (Text)
DepartamentEmployeestName (Primary Name Column) 1 => N It_Employees


It_Employees

EmployeeCode (Text)
EmployeeFullName (Primary Name Column) 1 => N It_Incidents
EmployeeEmail (Text)
EmployeeActive (Choice) (Yes/No)
DepartamentEmployees (LookUp) N => 1 It_DepartamentEmployees



It_Incidents

IncidentCode (Text)
IncidentTitle (Primary Name Column) 1 => N It_IncidentsTechnicians / It_IncidentHistory
IncidentDescription (Text Area)
IncidentCreateDate (Date)
IncidentCloseDate (Date)
IncidentStatus (Choice) (Pending / In Process / Close / Cancel)
Employee (LookUp) N => 1 It_Employees


It_IncidentsTechnicians

IncidentsTechniciansCode (Text)
Incident (LookUp) N => 1 It_Incidents
Tecnician (LookUp) N => 1 It_Technicians
IncidentsTechniciansDate (Date)



It_Technicians

TechnicianCode (Text)
TechniciansFullName (Primary Name Column)
TechniciansEmail (Text)
TechniciansActive (Choice) (Yes/No)
TechniciansMode (Choice) (Active / Leave)
DepartamentTecnniciansName (LookUp) N => 1 It_DepartamentTecnnicians

It_DepartamentTecnnicians

DepartamentTecnniciansCode (Text)
DepartamentTecnniciansName (Primary Name Column) 1 => N  It_Technicians


It_IncidentHistory

HistoryCode (Text)
HistoryChangeDate (Date) 
HistoryComment (Text Area)
Incident (LookUp) N => 1 It_Incidents


### RELACIONES:

It_DepartamentEmployees 1 => N It_Employees
It_Employees   N => 1 It_DepartamentEmployees

It_Employees  1 => N It_Incidents
It_ Incidents N => 1 It_Employees

It_Incidents 1 => N It_IncidentsTechnicians
It_IncidentsTechnicians N => 1 It_Incidents

It_Technicians 1 => N It_IncidentsTechnicians
It_IncidentsTechnicians N => 1 It_Technicians

It_DepartamentTecnnicians 1 => N It_Technicians
It_Technicians N => 1 It_DepartamentTecnnicians


It_Incidents 1 => N It_IncidentHistory
It_IncidentHistory N => 1 It_Incidents

