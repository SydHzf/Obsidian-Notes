___
- All the dimensions present in a schema must have nearly same slowly changing other-wise there will be high cardinality
- For SDC2
	- check unchanged rows
	- check changed rows 
	- check new rows
	- union all the rows with historic once