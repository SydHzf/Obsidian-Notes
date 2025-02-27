___

How to Optimize the Infrastructure?
- Going through whole process listing the cost and finding the root costing.
-  View on View, causing delay and processing cost. Using data modelling correctly can help
-  Make data real-time without any need can also be costly ( running snowflake whenever there is an event to process its data but if there are 60 events each after one minute then there will be an hour opening of snowflake which is very costly) it is better to make it batch-time if possible
- Bad data modeling (creating tables and their relation)
	- what actually exist
	- what is costing
	- where should we focus our energy