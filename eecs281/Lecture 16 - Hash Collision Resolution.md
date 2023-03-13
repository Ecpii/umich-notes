# Load Factor
$\alpha$ is the load factor of a resolution method.
# Separate Chaining
Resolve collisions by maintainig linked lists for each table index. You will have to perform a linear search on that linked list though.

If you have M linked lists, the number of comparisons for sequential search decreases by a factor of M. In a table with M lists and N keys, it is probable that the number of keys in each list is *close to* $\alpha = \dfrac{N}{M}$ if the hash function is good.

In separate chaining, $\alpha$ is the average number of items per list, and as thus $\alpha$ can be $> 1$.

## Complexity
Insert: $O(1)$ if duplicates allowed, $O(\alpha)$ if not
Search: $O(\alpha)$
Remove: $O(\alpha)$
If we choose $M \approx N$, we get $O(\alpha) \approx O(1)$.

## Potential Mutations
- use vectors instead of linked lists
	- insertion is always $O(\alpha)$
	- search is now $O(\log \alpha)$
	- memory overhead increased
- use binary search trees instead of linked lists
	- $O(\log \alpha)$ insert and search as long as tree is balanced
	- large memory overhead
# Open Addressing
On inserting - if the spot in the table is used, go to the next open spot. On search, remember the general area where you should be, then linear search the area for your data. This works because you store the key where you put the value.
## Probing
Probing is the act of checking by index in the hash table. There are three possible outcomes:
- empty - no data
- hit - probe finds occupied location and key there matches probe key
- full - probe finds something that doesn't match
If probe results in full, then probe at next spot until a hit or empty.
Mathematically, linear probing is trying:
$$
\text{index} = 
\begin{cases}
	t(\text{key}) \mod M &\text{} \\
	t(\text{key + 1}) \mod M &\text{if previous was full} \\
	t(\text{key + 2}) \mod M &\text{if previous was full} \\
	t(\text{key + 3}) \mod M &\text{if previous was full} \\
	 \vdots & \vdots \\
	t(\text{key + }j) \mod M &\text{if previous was full}, j \in \mathbb{N} \\
\end{cases}
$$

## Clusters
A cluster is a contiguous group of occupied table cells. For probing, the best case is having many clusters that have empty cells in them. The worst case is that all the full items are contiguous and all the empty ones are contiguous.

## Deletion
Issue: a cell before your cell but after the hash location is deleted. The probe will hit an empty and assume your item doesn't exist even though it's just after the empty.

The solution to this is that we mark the deleted element as deleted (different from empty), so that we can handle it differently.
An insertion probe will consider a deleted item as a miss and and consider it usable (if they key dones't already exist elsewere) A search considers it occupied (ful) and keeps searching.

Marking something as deleted is best done with an `enum` (two `bool`s also works, but takes up more space and isnt as well named.)

## Counting Probes
The work factor $\alpha$ for open addressing is the percentage of table indices occupied. $\alpha \le 1$.
If you have a hash table of size $M$ that contains $N = \alpha M$, you will have to do
$$
\text{average probes} = 
\begin{cases}
	\dfrac{1}{2}\left(1 + \dfrac{1}{1 - \alpha}\right) &\text{probes for hits} \\
	\dfrac{1}{2}\left(1 + \dfrac{1}{(1 - \alpha)^2}\right) &\text{probes for misses} \\
\end{cases}
$$
Intuitively, this means that the more full your table is, the more average probes you will need to take to get a hit. It takes even more for a miss.
| $\alpha$ | Average probes: successful search | Average probes: unsuccessful search |
| -------- | --------------------------------- | ----------------------------------- |
| 0.1      | 1.1                               | 1.1                                 |
| 0.2      | 1.1                               | 1.1                                 |
| 0.3      | 1.2                               | 1.5                                 |
| 0.4      | 1.3                               | 1.9                                 |
| **0.5**  | **1.5**                           | **2.5**                             |
| 0.6      | 1.8                               | 3.6                                 |
| 0.7      | 2.2                               | 6.1                                 |
| 0.8      | 3.0                               | 13.0                                |
| 0.9      | 5.5                               | 50.5                                |
We can interpret a container that is half full as full in order to prevent more exponential behavior.

## Quadratic Probing
In quadratic probing, we instead add the square of an increment. This increases performance by increasing gaps between items (making clusters smaller).
Mathematically, quadratic probing is trying:
$$
\text{index} =
\begin{cases}
	t(\text{key}) \mod M &\text{} \\
	t(\text{key + 1}) \mod M &\text{if previous was full} \\
	t(\text{key + 4}) \mod M &\text{if previous was full} \\
	t(\text{key + 16}) \mod M &\text{if previous was full} \\
 \vdots &\vdots \\
	t(\text{key + }j^2) \mod M &\text{if previous was full, }j \in \mathbb{N} \\
\end{cases}
$$

The calculation above for quadratic probes gives you average probes of:
$$
\text{average probes} = 
\begin{cases}
	1 - \dfrac{\alpha}{2} + \ln\left(\dfrac{1}{1 - \alpha}\right) &\text{probes for hits} \\
	\dfrac{1}{1 - \alpha} - \alpha + \ln\left(\dfrac{1}{1 - \alpha}\right) &\text{probes for misses} \\
\end{cases}
$$
| $\alpha$ | Average probes: successful search | Average probes: unsuccessful search |
| -------- | --------------------------------- | ----------------------------------- |
| 0.1      | 1.06                              | 1.12                                |
| 0.2      | 1.12                              | 1.27                                |
| 0.3      | 1.21                              | 1.49                                |
| 0.4      | 1.31                              | 1.78                                |
| **0.5**  | **1.44**                          | **2.19**                            |
| 0.6      | 1.62                              | 2.82                                |
| 0.7      | 1.85                              | 3.84                                |
| 0.8      | 2.21                              | 5.81                                |
| 0.9      | 2.8                               | 11.40                                |

## Double Hashing
Use a second hash function to calculate the interval:
$$
\text{index} =
\begin{cases}
	t(\text{key}) \mod M &\text{} \\
	t(\text{key + }t^{'}(key)) \mod M &\text{if previous was full, }j \in \mathbb{N}, t^{'}\text{ is another hash}
\end{cases}
$$
# Dynamic Hashing
Once you run out of space (or we logically say it is full), we need to increase the space of the hash table. In either collision resolution strategy we have, doubling the size of the table will degrade search performance.

## Simple Dynamic Hashing
Double the size of the table, and then rehash everything into the new table.

Assuming that we logically declare a table that is half full (M = 0.5) as full,
When you insert into your table until its full, you are always peforming an insertion where $\alpha \le 0.5$. With worst case analysis, we assume that $\alpha = 0.5$ and use the value in the table for unsuccessful searching (2.5 for linear, 2.19 for quadratic), to see that it took
$$
\text{probes for insertions} = 2.5 * (\dfrac{M}{2} - 1) = O(M)
$$
When we insert the $M/2$th item to make our original table full, we move everything into the new table. This is now inserting into a $M/4$ full table. Again, use the value in the table for $\alpha = .25 \approx .3$, and we get
$$
\text{probes for insertion into new table} = 1.5 * \dfrac{M}{2} = O(M)
$$
Since all of these operations are $O(M)$, and we do $M/2$ insertions, the amortized complexity of insertion using this is:
$$
M / \dfrac{M}{2} = 2 = O(1)
$$

