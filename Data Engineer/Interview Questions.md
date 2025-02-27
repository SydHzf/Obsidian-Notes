1. Tell me about your self
	1. about education / experience
	2. Achievements
	3. why to fit in 
2. Class is a blue-print which does not carry any memory on run-time.
3. Object allocated memory on run-time.
4. Constructor chaining is one constructor invoking other constructor of the same class.
5.  Abstraction is about expressing external simplicity, and Encapsulation is about hiding internal complexity.
6. There are two-way to add functionality of one class into other
	- [[4 Pillars | Inheritance]]
	- Composition
7. copy operator will create separate memory allocation, while = operator will only assign reference of one to another.
8. Coupling is dependence of one object onto others.
9. Overloading is a concept which employs two or more methods in a class with the Same name but different method signature, compile time polymorphism
10. if a method with the same method signature is present in both child and parent, method overriding, run-time polymorphism.
11. To connect local machine to database
```python
from airflow import DAG
from airflow.operators.python_operator import PythonOperator
from airflow.hooks.mysql_hook import MySqlHook
from airflow.utils.dates import days_ago
import pandas as pd

# Define default arguments for the DAG
default_args = {
    'owner': 'airflow',
    'depends_on_past': False,
    'start_date': days_ago(1),
    'retries': 1,
}

# Initialize the DAG
dag = DAG(
    'mysql_to_csv',
    default_args=default_args,
    description='Fetch data from MySQL and save to CSV',
    schedule_interval=None,  # Change as needed for your schedule
)

# Function to fetch data from MySQL and save to CSV
def fetch_data_from_mysql_and_save_to_csv():
    # Initialize MySqlHook
    mysql_hook = MySqlHook(mysql_conn_id='your_mysql_connection_id')  # Use your connection ID

    # Execute the query
    sql = "SELECT * FROM your_table_name"  # Replace with your table name
    connection = mysql_hook.get_conn()
    cursor = connection.cursor()
    cursor.execute(sql)
    rows = cursor.fetchall()
    columns = [desc[0] for desc in cursor.description]

    # Convert to DataFrame
    df = pd.DataFrame(rows, columns=columns)

    # Save DataFrame to CSV
    csv_file_path = '/path/to/your_local_file.csv'  # Specify your local file path
    df.to_csv(csv_file_path, index=False)

    cursor.close()
    connection.close()

# Define the PythonOperator to run the function
fetch_data_task = PythonOperator(
    task_id='fetch_data_from_mysql_and_save_to_csv',
    python_callable=fetch_data_from_mysql_and_save_to_csv,
    dag=dag,
)

# Set the task dependencies
fetch_data_task

```

12.  