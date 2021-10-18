# payroll_api
An API focused on uploading payroll data and outputting detailed employee pay period reports.



1) Upload a CSV file containing data on the number of hours worked per day per employee 
* Each CSV file is known as a time report and will contain:
   ** A header, denoting the columns in the sheet (date, hours worked, employee id, job group)
   ** 0 or more data rows
* time-report-42.csv would represent a report with an ID of 42




2) Retrieve a report detailing how much each employee should be paid in each pay period
 * Employees are paid by the hour
 * 2 JobGroups: 1) A gets paid $20/hr, B is paid $30/hr
 * Employees are identified by a "employee id" field



Assumptions:
    * File names are correct format (time-report-{id}.csv)
    * Files are well formed with correct data 



{
  "payrollReport": {
    "employeeReports": [
      {
        "employeeId": "1",
        "payPeriod": {
          "startDate": "2020-01-01",
          "endDate": "2020-01-15"
        },
        "amountPaid": "$300.00"
      },
      {
        "employeeId": "1",
        "payPeriod": {
          "startDate": "2020-01-16",
          "endDate": "2020-01-31"
        },
        "amountPaid": "$80.00"
      },
      {
        "employeeId": "2",
        "payPeriod": {
          "startDate": "2020-01-16",
          "endDate": "2020-01-31"
        },
        "amountPaid": "$90.00"
      }
    ]
  }
}





Tips and tricks:

1) Since reports cant be modified, we could aggregate time_report data into the time_report database (sum up all hours worked, wage, etc as aggregate columns)