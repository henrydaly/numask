NUMASK: High Performance Scalable Skip List for NUMA
-----------------------------------------------------
Built off the No Hot Spot Non-blocking Skip List (courtesy of Crain, 
Gramoli, and Raynal), this data structure was designed to exploit the
characteristics of Non-Uniform Memory Access (NUMA) architectures to 
improve performance. NUMASK has been integrated into Vincent Gramoli's 
synchrobench (https://github.com/gramoli/synchrobench) and can be tested
against other lock-free skip lists using the micro benchmark suite. 

If you use NUMASK, please cite the associated paper:
H. Daly, A. Hassan, M. Spear, R. Palmieri. NUMASK: High Performance Scalable Skip List for NUMA. DISC 2018.

Parameters
---------
 - t, the number of application threads to be spawned. Note that this does not necessarily represent all threads, as it excludes JVM implicit threads and extra maintenance threads spawned by some algorithms.
 - i, the initial size of the benchmark. This corresponds to the amount of elements the data structure is initially fed with before the benchmark starts collecting statistics on the performance of operations.
 - r, the range of possible keys from which the parameters of the executed operations are taken from, not necessarily uniformly at random. This parameter is useful to adjust the evolution of the size of the data structure.
 - u, the update ratio that indicates the amount of update operations among all operations (be they effective or attempted updates).
 - f, indicates whether the update ratio is effective (1) or attempted (0). An effective update ratio tries to match the update ratio to the total amount of operations that effectively modified the data structure by writing, excluding failed updates (e.g., a remove(k) operation that fails because key k is not present).
 - A, indicates whether the benchmark alternates between inserting and removing the same value to maximize effective updates. This parameter is important to reach a high effective update ratios that could not be reached by selecting values at random.
 - U, the unbalance parameter that indicates the extent to which the workload is skewed towards smaller or larger values. This parameter is useful to test balanced structure like trees under unbalancing workloads (not available on all benchmarks).
 - d, the duration of the benchmark in milliseconds.
 - a, the ratio of write-all operations that correspond to composite operations. Note that this parameter has to be smaller or equal to the update ratio given by parameter u.
 - s, the ratio of snapshot operations that scan multiple elements of the data structure. Note that this parameter has to be set to a value lower than or equal to 100-u, where u is the update ratio.
 - x, the alternative synchronization technique for the same algorithm. In the case of transactional data structures, this rep- resents the transactional model used (relaxed or strong) while it represents the type of locks used in the context of lock-based data structures (optimistic or pessimistic). 
