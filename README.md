# Pewlett-Hackard-Analysis

## ERD

![Employee Database Outline](https://github.com/travgreenfield/Pewlett-Hackard-Analysis/blob/master/EmployeeDB.png?raw=true)

## Technical Analysis

### Project Overview

Pewlett Hackard is a large company on the verge of a significant wave of retirements. In order to protect themselves from an unexpected need for new hires, we ran an analysis to determine the amount of employees that are likely to leave, their associated titles, and potential current employees to mentor and fill these positions. 

### Database Creation

By creating tables to house the six csv files provided, linking them using common data points, and filtering for the employees we're analyzing (particularly by age), we were able to extract useful, actionable data.

### Summary of Results

- For a more zoomed-out apporach, we were able to gather (as organized in the "retirement_age_employees" table) that there are 72,458 employees at an age where we can expect them to retire shortly.

- We can see which positions are likely to be hit most heavily by the upcoming retirements. As highlighted in the "employees_per_title_retiring" csv, both the Senior Engineer and Senior Staff positions are facing significant losses.

- We were also able to gather data that allows the organization to take immediate steps, including highlighting specific employees that are eligible for an upcoming mentorship program and providing that table in the form of the "aggregated_mentorship_info" csv.

### Challenges

In gathering the "employees set to retire by department" data, it revealed the differences in which the "to_date" information in was used differently between the initial set of data we received. By consulting the original ERD to draw new relationships between tables (using the Join statements below), we were able to utilize the information available to filter for employee's current titles.

*SELECT ce.emp_no,
ce.first_name,
ce.last_name,
s.from_date,
s.salary,
ti.title,
ti.to_date
INTO retiring_by_title
FROM current_emp as ce
INNER JOIN salaries as s
ON (ce.emp_no = s.emp_no)
INNER JOIN titles AS ti
ON (ti.emp_no = ce.emp_no);*

### Further Analysis Requests

While this analysis did a great job in highlighting the specific positions being vacated, a further deep dive into the department-specific exits would be helpful. As there may be different hiring, training, and onboarding timelines for the various positions, that information will allow us to demonstrate when these hirings need to take place.
