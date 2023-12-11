
# Permutations Without Repetition

**A science exhibition is organized in a school, where students can display their projects. The organizing committee has selected 5 unique projects from different students to be showcased in the main hall. However, due to space constraints, they can only display one project at a time. The committee decides to change the display every day so that each project gets an equal opportunity to be showcased. How many different ways can the committee arrange the display schedule for these 5 projects over 5 days, assuming each project is displayed exactly once during this period?**


```Python
import math

# Number of projects
n = 5

# Calculating the number of different permutations
num_permutations = math.factorial(n)
num_permutations

```

The number of different ways the committee can arrange the display schedule for the 5 projects over 5 days is 120.

**A classroom of 16 students has 16 seats. How many possibilities are there for seating?**


```Python
import math

#number of seats
n = 16

#calculating the number of permutations
num_of_permutations = math.factorial(n)
num_of_permutations
```

There are 20922789888000 ways to seat the students.

**A group of 6 friends decides to take a photo together. In how many different ways can they stand in a line for the photo, assuming each friend stands in the photo exactly once?**


```Python
import math

#number of seats
n = 6

#calculating the number of permutations
num_of_permutations = math.factorial(n)
num_of_permutations
```


**In a chess tournament, there are 8 players competing in the first round. The tournament organizer wants to know how many different ways the first-round matchups can be arranged, assuming each player is paired with exactly one other player for a total of 4 matches.**

You have to arrange 8 players into 4 pairs. This is equivalent to finding the permutations of 8 items taken 2 at a time, repeatedly. This can be solved using the formula $P_{8,2}=\frac{8 !}{(8-2) !}$, and then dividing the result by 4 ! to account for the indistinguishability of the pairs.

```Python

```


**A teacher has a set of 7 different books to distribute as prizes to her students. She decides to give these books to the top 3 students in her class. In how many different ways can she distribute these books?**


```Python

```

Here, we need to calculate the number of permutations of 7 items taken 3 at a time. This can be calculated using the formula $P_{7,3}=\frac{7 !}{(7-3) !}$.

**A digital lock uses a 4-digit code where each digit can range from 0 to 9. However, each digit must be unique. How many different combinations can be created for this lock?**

You need to calculate the number of ways to arrange 4 unique digits out of 10 ( 0 to 9 ). This can be calculated using permutations, where $n=10$ and you're choosing 4 at a time: $P_{10,4}=\frac{10 !}{(10-4) !}$.

