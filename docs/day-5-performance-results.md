| Metric 	| Result |
| Users 	| 10 	 |
| Ramp-up 	| 10 sec |
| Loops 	| 5 	 |


Label						# Samples	Average	Min		Max		Std. Dev.	Error %	Throughput	Received KB/sec	Sent KB/sec	Avg. Bytes
01 - Authenticate			50			380		223		1054	291.37		0.00%	0.51426		0.39			0.12		771.4
02 - Get Booking			50			711		663		1121	67.05		0.00%	0.5161		29.35			0.07		58224.2
03 - Create Booking			50			234		223		270		8.3			0.00%	0.51847		0.48			0.22		950
04 - Update Booking			50			244		223		670		61.29		0.00%	0.5184		0.47			0.24		924.3
05 - Get Updated Booking	50			339		222		782		199.53		0.00%	0.51834		0.47			0.08		924
Booking Workflow			50			1911	1558	2958	341.85		0.00%	0.42133		25.43			0.6			61794
TOTAL						300			637		222		2958	625.78		0.00%	2.52795		50.85			1.2			20598
