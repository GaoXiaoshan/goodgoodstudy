[toc]

## H-index

### Problem

Jorge is a physicist who has published many research papers and wants to know how much impact they have had in the academic community. To measure impact, he has developed a metric, [H-index](https://en.wikipedia.org/wiki/H-index), to score each of his papers based on the number of times it has been cited by other papers. Specifically, the *H-index score* of a researcher is the largest integer HH such that the researcher has HH papers with at least HH citations each.

Jorge has written NN papers in his lifetime. The ii-th paper has CiCi citations. Each paper was written sequentially in the order provided, and the number of citations that each paper has will never change. Please help Jorge determine his *H-index score* after each paper he wrote.

### Input

The first line of the input gives the number of test cases, TT. TT test cases follow. Each test case begins with a line containing NN, the number of papers Jorge wrote. The second line contains NN integers. The ii-th integer is CiCi, the number of citations that the ii-th paper has.

### Output

For each test case, output one line containing `Case #xx: yy`, where xx is the test case number (starting from 11) and yy is a space-separated list of NN integers. The ii-th integer is Jorge's *H-index* score after writing his ii-th paper.

### Limits

Time limit: 50 seconds.
Memory limit: 1 GB.

1≤T≤100
1≤Ci≤10^5

#### Test Set 1

1≤N≤1000

#### Test Set 2

1≤N≤10^5

### Sample

Sample Input

```
2
3
5 1 2
6
1 3 3 2 2 15
```



Sample Output

```
Case #1: 1 1 2
Case #2: 1 1 2 2 2 3
```

The input contains 2 test cases. In Sample Case #1, Jorge wrote NN = 3 papers.

- After the 1st paper, Jorge's *H-index* score is 1, since he has 1 paper with at least 1 citation.
- After the 2nd paper, Jorge's *H-index* score is still 1.
- After the 3rd paper, Jorge's *H-index* score is 2, since he has 2 papers with at least 2 citations (the 1st and 3rd papers).

In Sample Case #2, Jorge wrote NN = 6 papers.

- After the 1st paper, Jorge's *H-index* score is 1, since he has 1 paper with at least 1 citation.
- After the 2nd paper, Jorge's *H-index* score is still 1.
- After the 3rd paper, Jorge's *H-index* score is 2, since he has 2 papers with at least 2 citations (the 2nd and 3rd papers).
- After the 4th paper, Jorge's *H-index* score is still 2.
- After the 5th paper, Jorge's *H-index* score is still 2.
- After the 6th paper, Jorge's *H-index* score is 3, since he has 3 papers with at least 3 citations (the 2nd, 3rd and 6th papers).



### Solution

```python
def h_index(n, citations):
  ans = []
  # TODO: Complete the function to get the H-Index scores after each paper

  return ans


if __name__ == '__main__':
  t = int(input())

  for test_case in range(1, t + 1):
    n = int(input())                      # The number of papers
    citations = map(int, input().split()) # The number of citations for each paper
    h_index_scores = h_index(n, citations)
    print("Case #" + str(test_case) + ": " + ' '.join(map(str, h_index_scores)))

```



## Hex

### Problem

This problem was inspired by a board game called Hex, designed independently by Piet Hein and John Nash. It has a similar idea, but does not assume you have played Hex.

This game is played on an N×NN×N board, where each cell is a hexagon. There are two players: Red side (using red stones) and Blue side (using blue stones). The board starts empty, and the two players take turns placing a stone of their color on a single cell within the overall playing board. Each player can place their stone on any cell not occupied by another stone of any color. There is no requirement that a stone must be placed beside another stone of the same color. The player to start first is determined randomly (with equal probability among the two players).

The upper side and lower sides of the board are marked as red, and the other two sides are marked as blue. For each player, the goal of the game is to connect the two sides marked with their color by forming a connected path using stones of their color. The first player to achieve this wins. Note that the four corners are considered connected to both colors.

The game ends immediately when one player wins.

Given a game state, help someone new to the game determine the status of a game board. Say one of the following:

- `Impossible`: If it was impossible for two players to follow the rules and to have arrived at that game state.
- `Red wins`: If the player playing the red stones has won.
- `Blue wins`: If the player playing the blue stones has won.
- `Nobody wins`: If nobody has yet won the game. Note that a game of Hex cannot end without a winner!



Note that in any impossible state, the only correct answer is `Impossible`, even if red or blue has formed a connected path of stones linking the opposing sides of the board marked by their colors.

Here is a an example game on a 6×66×6 gameboard where blue won. Blue was the first player to move, and placed a blue stone at cell marked as 11. Then Red placed at cell 22, then blue at cell 33, etc. After the 1111-th stone is placed, blue wins.

<img src="/Users/gaoshan/Library/Application Support/typora-user-images/截屏2022-02-18 上午9.44.21.png" alt="截屏2022-02-18 上午9.44.21" style="zoom:33%;" />



### Input

The first line of input gives the number of test cases, TT. TT test cases follow. Each test case start with the size of the side of the board, NN. This is followed by a board of NN rows and NN columns consisting of only `B`, `R`, and `.` characters. `B` indicates a cell occupied by blue stone, `R` indicates a cell occupied by red stone, and `.` indicates an empty cell.

### Output

For each test case, output one line containing `Case #xx: yy`, where xx is the case number (starting from 11) and yy is the status of the game board. It can be `"Impossible"`, `"Blue wins"`, `"Red wins"`, or `"Nobody wins"` (excluding the quotes). Note that the judge is case-sensitive, so answers of `"impossible"`, `"blue wins"`, `"red wins"`, and `"nobody wins"` will be judged incorrect.

### Limits

Time limit: 30 seconds.
Memory limit: 1 GB.
1≤T≤100

#### Test Set 1

1≤N≤10

#### Test Set 2

1≤N≤100

### Sample

Sample Input

```
7
1
.
1
B
1
R
2
BR
BB
4
BBBB
BBB.
RRR.
RRRR
4
BBBB
BBBB
RRR.
RRRR
6
......
..R...
BBBBBB
..R.R.
..RR..
......
```



Sample Output

```
Case #1: Nobody wins
Case #2: Blue wins
Case #3: Red wins
Case #4: Impossible
Case #5: Blue wins
Case #6: Impossible
Case #7: Blue wins
```



### Solution

```python
def game_status(board_size, board):
  # TODO: implement this method to determine the status of the game board
  return ""

def main():
  test_cases = int(input())
  for test_case in range(1, test_cases + 1, 1):
    board_size = int(input())
    board = []
    for _ in range(board_size):
      board.append(list(input().strip()))

    ans = game_status(board_size, board)

    print("Case #{}: {}".format(test_case, ans))

if __name__ == "__main__":
  main()

```



## Milk Tea

### Problem

The milk tea in China is very delicious. There are many binary ("either-or") options for customizing a milk tea order, such as:

- "with ice" OR "no ice"
- "with sugar" OR "no sugar"
- "with bubbles" OR "no bubbles"
- "with pudding" OR "no pudding"
- and so on.

A customer's preferences for their milk tea can be represented as a binary string. For example, using the four properties above (in the order they are given), the string `1100` means "with ice, with sugar, no bubbles, no pudding".

Today, Shakti is on duty to buy each of his NN friends a milk tea, at a shop that offers PP binary options. But after collecting everyone's preferences, Shakti found that the order was getting too complicated, so Shakti has decided to buy the same type of milk tea for everyone. Shakti knows that for every friend, for every preference that is not satisfied, they will complain once. For example, if two of the friends have preferences for types `101` and `010`, and Shakti chooses type `001`, then the first friend will complain once and the second friend will complain twice, for a total of three complaints.

Moreover, there are MM different forbidden types of milk tea that the shop will not make, and Shakti cannot choose any of those forbidden types.

What is the smallest number of complaints that Shakti can get?

### Input

The first line of the input gives the number of test cases, TT. TT test cases follow. Each test case starts with a line containing 3 integers NN, MM, and PP, as described above. Then, there are NN more lines, each of which contains a binary string; these represent the preferences of the NN friends. Finally, there are MM more lines, each of which contains a binary string; these represent the forbidden types of milk tea that the shop will not make. Binary strings consist only of `0` and/or `1` characters.

### Output

For each test case, output one line containing `Case #x: y`, where `x` is the test case number (starting from 11) and `y` is the minimum number of complaints that Shakti can get, per the rules described above.

### Limits

Time limit: 30 seconds.
Memory limit: 1 GB.

1≤T≤100
All of the forbidden types of milk tea are different.



#### Test Set 1

1≤N≤10
1≤M≤min(10, 2^P−1)
1≤P≤10

#### Test Set 2

1≤N≤100
1≤M≤min(100,2^P−1)
1≤P≤100



### Sample

Sample Input

```
2
3 1 4
1100
1010
0000
1000
2 4 4
1111
1111
1111
0111
1011
1101
```

Sample Output

```
Case #1: 4
Case #2: 2
```

In Sample Case #1, there are 3 friends, and they want milk teas of types `1100`, `1010`, and `0000`. If Shakti could choose type `1000`, then each friend would complain once, for a total of 3 complaints. However, type `1000` is not available in the shop. So, given these constraints, an optimal solution is to choose type `1100`. Then, his friends will complain 0, 2, and 2 times, respectively, for a total of 4 complaints.

In Sample Case #2, Shakti's best option is to choose type `1110`. Each friend will complain once, for a total of 2 complaints. Notice that different friends might have the same preferences. Also notice that the limits for both the Small and Large datasets guarantee that there is always at least one possible type of milk tea that is not forbidden.



### Solution

```python
"""Starter Code for Milk Tea CC Problem"""

# Complete the count_complaints function
def count_complaints(preferences, forbiddens):
  complaints = 0
  # TODO: Add logic to count the number of complaints
  return complaints

if __name__ == '__main__':
  # Read number of test cases
  num_cases = int(input())

  for tc in range(1, num_cases + 1):
    # Read number of friends, number of forbidden teas, and number of options
    num_friends, num_forbidden, num_options = map(int, input().split())

    # Read the friends' preferences
    preferences = [input() for _ in range(num_friends)]

    # Read the forbidden teas
    forbiddens = [input() for _ in range(num_forbidden)]

    print("Case #%d: %d" % (tc, count_complaints(preferences, forbiddens)))

```

