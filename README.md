# thread_numbers_generator
Test task on C++

On high level, the task must generate/create all numbers in the range 1-N via random generation. Usage of RAM must be limited (i.e. it should not grow unrestrictedly). Multithreaded approach must be used.

Implement an application which will do the following:

1)	Application must accept one parameter from command line:
a)	N – number of elements to generate. It must be positive integer not larger than RAND_MAX (if this is not true – application must exit with error description).
2)	Create a queue (FIFO – first in, first out) which will store positive integers.
3)	One/first “producer” thread (you could create new or use main one) will be generating random numbers (value in the range between 1 – N) and will be adding/pushing these numbers to the queue. The size of the queue must not exceed some specified limit (i.e. limited by constant variable with default value 1000). It makes sense to pause generating of numbers if the queue is full (however it is up to you how to implement it).
4)	Create a storage which will store N elements with following attributes:
a)	Number itself (positive integer)
b)	Number of microseconds it took to generate it (positive integer)
c)	Order by which the number was generated (it will be 1-N number).
5)	Another/second “consumer” thread must do the following: 
a)	Read values from the queue (populated with “producer” thread) and check if this number/element already exists in the storage:
i)	If yes – then simply discard this number.
ii)	If not – add new number/element to the storage. Calculate the time (the number of microseconds) which is the difference between current time and the time when previous number was added (i.e. how much time it took to find/add this new randomly generated number). Print (in console) the line with fixed length format which must contain all element attributes. Note: you could use/modify attached time_counter.h or do your own implementation.
6)	Stop execution when all possible numbers in the range between 1 – N will be generated (i.e. every cell in the storage will be populated with correposnded number).
7)	Calculate and print the average time it took to generate a number. Exit application.
