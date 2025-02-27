___
![[Pasted image 20241231125527.png]]
`step 1` : doing group by hourly, sum and count to aggregate duplicate and using collect_list for metadata of may be different duplicates
`step 2` : doing the earlier and latest full join again and again from 0 to 23 (hours)