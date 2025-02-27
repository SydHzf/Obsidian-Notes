___
Think of this as a few Who, What, Where, When, and How
1. "Who" fields are usually pushed out as IDs (this user clicked this button, we
     only hold the user_id not the entire user object)
2.  "Where" fields
         Most likely modeled out like Who with "IDs" to join, but more likely to bring in dimensions,
         especially if they're high cardinality like "device_id"
3. "How" fields
         How fields are very similar to "Where" fields. "He used an iphone to make this click"
4. "What" fields are fundamentally part of the nature of the fact.
     In notification world - "GENERATED", "SENT", "CLICKED", "DELIVERED"
 5. "When" fields are fundamentally part of the nature of the fact
     Mostly an "event_timestamp" field or "event_date"