___
- *Normalization vs Denormalization*
    - Normalized facts don't have any dimensional attributes, just IDs to join to get that information (can be slower) . if we can query costlessly
    - Denormalized facts bring in some dimensional attributes for quicker analysis at the cost of more storage (can cause duplication)
    Both normalized and denormalized facts have a place in this world!
- *raw Logs and fact table are married*
	Fact data and raw logs are the same thing
  1.  Raw logs
	-  Ugly schemas designed for online systems that make data analysis sad
	- Potentially contains duplicates and other quality errors
	- Usually have shorter retention
  1.  Fact data
	  - Nice column names
	  - Quality guarantees like uniqueness, not null, etc
	  - Longer retention
	        
Logging brings in all the critical context for your fact data
- Usually done in collaboration with online system engineers
 Don't log everything!
- Log only what you really need
 Logging should conform to values specified by the online teams
- Thrift is what is used at Airbnb and Netflix for this

- *Fact data should be*
	- Fact datasets should have quality guarantees
	- If the didn't, analysis would just go to the raw logs!
	- Fact data should generally be smaller than raw logs
	- Fact data should parse out hard-to
![[extras/fact-data-modeling-day-1-jade-wilson.pdf]]