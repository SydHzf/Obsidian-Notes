___
Graph modeling is RELATIONSHIP focused, not ENTITY focused.
Because of this, you can do a very poor job at modeling the entities
- Usually the model looks like
	 Identifier: STRING
	 Type: STRING
	 Properties: MAP<STRING, STRING>

The relationships are modeled a little bit more in depth
- Usually the model looks like
	  subject_identifier: STRING
	  Subject_type: VERTEX_TYPE
	  Object_identifier: STRING
	  Object_type: VERTEX_TYPE
	  Edge_type: EDGE_TYPE
	  Properties: MAP<STRING, STRING>
		 