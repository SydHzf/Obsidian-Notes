___
Gate Smasher 73 onward [Transaction](https://www.youtube.com/playlist?list=PLxCzCOWd7aiFAN6I8CuViBuCdJgiOkT2Y)
**Definition:** A transaction generally represents change  in database.
**Operations**: Read from storage in RAM, Write in RAM, Commit execute whatever operation are performed in Storage.  
**Properties**
	[ACID](https://youtu.be/GAe5oB742dw)
- Atomicity → Either all or None (if fail in after applying commit all the execution rollback) ^69485e
- Consistency → Before transaction start and after it is completed, the sum of transfer remain same.
- Isolation → Convert parallel execution into serial.
- Durability → Change must be constant.
**Scheduler:**
- Serial → One after another execution of transaction (>> Performance → >> Throughput)
- Parallel → Switching between transaction
**Problems In Parallel Scheduler:**
- Dirty-read → Reading data from unsuccessful transaction.
- Unrepeatable-read →  when (read > logical operation > write) one transaction is commit before other, same change will be done in db twice. 
