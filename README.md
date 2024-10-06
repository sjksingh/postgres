# postgres
Database Utility Functions

This repository contains various PostgreSQL functions designed to monitor and report on the health and activity of the database. These functions are intended to provide insights into database performance, vacuuming, and other key metrics, allowing database administrators to manage and maintain databases effectively.

Table of Contents

Getting Started
Function Descriptions
get_database_activity()
get_database_health()
get_vacuum_activity()
License
Contributing
Getting Started

To use these functions, you need to create them in your PostgreSQL database. You can execute the SQL code provided in each function's respective section to create the functions. Once created, you can run each function directly within a SQL query.

Usage
To execute a function and retrieve the results, use the following syntax within a PostgreSQL client such as psql:

sql
Copy code
SELECT * FROM function_name();
Replace function_name with the name of the function you wish to execute, e.g., get_database_activity().

Function Descriptions

get_database_activity()
This function provides information on database activity, including top wait events, the most active tables, slow queries, and long-running queries. It is useful for identifying areas that may need optimization.

Parameters:
activity_threshold (optional, integer) - The threshold for the minimum number of operations to be included in the output.
Output Columns:
description: A brief description of the metric.
result: The metric's value or details.
Example:
sql
Copy code
SELECT * FROM get_database_activity(10);
get_database_health()
This function reports on the general health of the database, including host information, database mode, uptime, cache hit ratio, and more. It helps in tracking the overall status and identifying potential issues early.

Parameters:
dead_tuple_threshold (optional, integer) - Minimum number of dead tuples for the function to report tables that may require vacuuming.
Output Columns:
description: A brief description of the metric.
result: The metric's value or details.
Example:
sql
Copy code
SELECT * FROM get_database_health(100);
get_vacuum_activity()
This function provides insights into vacuum activities within the database, such as the last vacuum timestamps, tables with the most dead tuples, and vacuum-related locks. This is especially useful for understanding how vacuuming is affecting database performance and which tables may need manual intervention.

Parameters:
vacuum_threshold (optional, integer) - Minimum number of dead tuples for a table to be reported.
Output Columns:
description: A brief description of the metric.
result: The metric's value or details.
Example:
sql
Copy code
SELECT * FROM get_vacuum_activity(1000);
License

This project is licensed under the MIT License - see the LICENSE file for details.

Contributing

We welcome contributions to expand the functionality of these PostgreSQL utilities. Please submit a pull request or open an issue to suggest a new function or improvement.
