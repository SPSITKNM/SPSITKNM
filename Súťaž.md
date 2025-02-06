# Announcement written by Tom. Muc. 

All tasks are written in English to enhance language skills and simulate a corporate environment where English is the universal language. Mastering English is a fundamental skill for professional growth and effective communication in the global workplace.

# Competition Rules  

1. **Teamwork**  
   - Participants will work in groups according to their seating rows.  

2. **Restrictions on AI Usage**  
   - The use of artificial intelligence (e.g., ChatGPT, Copilot, Gemini, Claude) is strictly prohibited.  

3. **Allowed Resources**  
   - Participants may use the following sources for reference:  
     - Stack Overflow  
     - Official documentation (e.g., MDN, Python Docs, W3Schools)  
     - Textbooks and lecture notes  
     - Any non-AI-generated online forums or articles  

4. **Fair Play & Integrity**  
   - Participants must work independently within their groups—no external help from individuals outside the competition.  
   - Any form of cheating or rule violation will result in disqualification.  

5. **Time Limit**  
   - The competition must be completed within the given time frame. No extra time will be provided.  

6. **Winner & Prize**  
   - The winning team will receive an **Exclusive Treska** as a reward.  

## Language Barrier Clause  
- In case of a language barrier, participants are required to use a translator to translate content into Slovak.  
- Recommended translators:  
  - [Google Translate](https://translate.google.com/)  
  - [DeepL Translator](https://www.deepl.com/translator)  
  - [Microsoft Translator](https://www.bing.com/translator)  
  - [Tomáš Mucha](https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.ferex.sk%2Fdetail%2Fkontajner-na-komunalny-odpad-1100-l-cierny&psig=AOvVaw3R8uQ9uL-q0F-e9brZtSD9&ust=1738957249595000&source=images&cd=vfe&opi=89978449&ved=0CBQQjRxqFwoTCKiIldzmr4sDFQAAAAAdAAAAABAE) 
 
# 1. Hans Red-Nosed Reports

Fortunately, the first location The Historians want to search isn't a long walk from the Chief Historian's office.

While the Red-Nosed Reindeer nuclear fusion/fission plant appears to contain no sign of the Chief Historian, the engineers there run up to you as soon as they see you. Apparently, they still talk about the time Rudolph was saved through molecular synthesis from a single electron.

They're quick to add that - since you're already here - they'd really appreciate your help analyzing some unusual data from the Red-Nosed reactor. You turn to check if The Historians are waiting for you, but they seem to have already divided into groups that are currently searching every corner of the facility. You offer to help with the unusual data.

## The unusual data (your puzzle input) consists of many reports, one report per line. Each report is a list of numbers called levels that are separated by spaces. For example:

```cpp
7 6 4 2 1
1 2 7 8 9
9 7 6 2 1
1 3 2 4 5
8 6 4 4 1
1 3 6 7 9
```
This example data contains six reports each containing five levels.

The engineers are trying to figure out which reports are safe. The Red-Nosed reactor safety systems can only tolerate levels that are either gradually increasing or gradually decreasing. So, a report only counts as safe if both of the following are true:

The levels are either all increasing or all decreasing.
Any two adjacent levels differ by at least one and at most three.
In the example above, the reports can be found safe or unsafe by checking those rules:
```cpp
7 6 4 2 1: Safe because the levels are all decreasing by 1 or 2.
1 2 7 8 9: Unsafe because 2 7 is an increase of 5.
9 7 6 2 1: Unsafe because 6 2 is a decrease of 4.
1 3 2 4 5: Unsafe because 1 3 is increasing but 3 2 is decreasing.
8 6 4 4 1: Unsafe because 4 4 is neither an increase or a decrease.
1 3 6 7 9: Safe because the levels are all increasing by 1, 2, or 3.
```
`So, in this example, 2 reports are safe.`

Analyze the unusual data from the engineers. How many reports are safe?

# 2. Adams Corrupted Memory

"Our computers are having issues, so I have no idea if we have any Chief Historians in stock! You're welcome to check the warehouse, though," says the mildly flustered shopkeeper at the North Pole Toboggan Rental Shop. The Historians head out to take a look.

The shopkeeper turns to you.  
*"Any chance you can see why our computers are having issues again?"*

The computer appears to be trying to run a program, but its memory (your puzzle input) is corrupted. All of the instructions have been jumbled up!

## Adams Understanding the Issue

It seems like the goal of the program is just to **multiply some numbers**.  
It does that with instructions like `mul(X,Y)`, where `X` and `Y` are each **1-3 digit numbers**. 

For example:
```plaintext
mul(44,46) → 44 × 46 = 2024  
mul(123,4) → 123 × 4 = 492  
```

## Corrupted Instructions

However, because the program's memory has been corrupted, there are also many invalid characters that should be ignored, even if they look like part of a mul instruction.

### Invalid examples:

- `` `mul(4*,` ``
- `` `mul(6,9!` ``
- `` `?(12,34)` ``
- `` `mul ( 2 , 4 )` ``

**These do nothing and should be ignored.**

## Example of Corrupted Memory

Consider the following section of corrupted memory:

```plaintext
xmul(2,4)%&mul[3,7]!@^do_not_mul(5,5)+mul(32,64]then(mul(11,8)mul(8,5)) 
```

Extracting Valid **mul** Instructions

The **four valid** mul instructions are:

```plaintext
mul(2,4)   → 2 × 4 = 8  
mul(5,5)   → 5 × 5 = 25  
mul(11,8)  → 11 × 8 = 88  
mul(8,5)   → 8 × 5 = 40  
```

Adding up the results : 

```plaintext
8 + 25 + 88 + 40 = 161
```

Scan the corrupted memory for uncorrupted `mul` instructions. What do you get if you add up all of the results of the multiplications?

# 3. Tewys Ceres Search 

"Looks like the Chief's not here. Next!" One of The Historians pulls out a device and pushes the only button on it. After a brief flash, you recognize the interior of the **Ceres monitoring station!**

As the search for the Chief continues, a small Elf who lives on the station tugs on your shirt; she'd like to know if you could help her with her word `search` (your puzzle input). She only has to find one word: `XMAS`.

This word search allows words to be horizontal, vertical, diagonal, written backwards, or even overlapping other words. It's a little unusual, though, as you don't merely need to find one instance of `XMAS` - you need to find `all of them`. Here are a few ways `XMAS` might appear, where irrelevant characters have been replaced with `.`:

```plaintext
..X...
.SAMX.
.A..A.
XMAS.S
.X....
```

### The actual word search will be full of letters instead. For example:

```plaintext
MMMSXXMASM
MSAMXMSMSA
AMXSXMAAMM
MSAMASMSMX
XMASAMXAMM
XXAMMXXAMA
SMSMSASXSS
SAXAMASAAA
MAMMMXMMMM
MXMXAXMASX
```

In this word search, XMAS occurs a total of 18 times; here's the same word search again, but where letters not involved in any XMAS have been replaced with `.`:

```plaintext
....XXMAS.
.SAMXMS...
...S..A...
..A.A.MS.X
XMASAMX.MM
X.....XA.A
S.S.S.S.SS
.A.A.A.A.A
..M.M.M.MM
.X.X.XMASX
```

Take a look at the little Elf's word search. `How many times does XMAS appear?`

# Wellick Resonant Collinearity

You find yourselves on the `roof` of a top-secret Easter Bunny installation.

While The Historians do their thing, you take a look at the familiar `huge antenna`. Much to your surprise, it seems to have been reconfigured to emit a signal that makes people 0.1% more likely to buy Easter Bunny brand Imitation Mediocre Chocolate as a Christmas gift! Unthinkable!

Scanning across the city, you find that there are actually many such antennas. Each antenna is tuned to a specific `frequency` indicated by a single lowercase letter, uppercase letter, or digit. You create a map (your puzzle input) of these antennas. For example:

```plaintext
............
........0...
.....0......
.......0....
....0.......
......A.....
............
............
........A...
.........A..
............
............
```

The signal only applies its nefarious effect at specific antinodes based on the resonant frequencies of the antennas. In particular, an antinode occurs at any point that is perfectly in line with two antennas of the same frequency - but only when one of the antennas is twice as far away as the other. This means that for any pair of antennas with the same frequency, there are two antinodes, one on either side of them.

So, for these two antennas with frequency `a`, they create the two antinodes marked with `#`:

```plaintext
..........
...#......
..........
....a.....
..........
.....a....
..........
......#...
..........
..........
```

Adding a third antenna with the same frequency creates several more antinodes. It would ideally add four antinodes, but two are off the right side of the map, so instead it adds only two:

```plaintext
..........
...#......
#.........
....a.....
........a.
.....a....
..#.......
......#...
..........
..........
```

Antennas with different frequencies don't create antinodes; `A` and `a` count as different frequencies. However, antinodes can occur at locations that contain antennas. In this diagram, the lone antenna with frequency capital `A` creates no antinodes but has a lowercase-`a`-frequency antinode at its location:

```plaintext
..........
...#......
#.........
....a.....
........a.
.....a....
..#.......
......A...
..........
..........
```

The first example has antennas with two different frequencies, so the antinodes they create look like this, plus an antinode overlapping the topmost `A`-frequency antenna:

```plaintext
......#....#
...#....0...
....#0....#.
..#....0....
....0....#..
.#....A.....
...#........
#......#....
........A...
.........A..
..........#.
..........#.
```

Because the topmost `A`-frequency antenna overlaps with a `0`-frequency antinode, there are `14` total unique locations that contain an antinode within the bounds of the map.

Calculate the impact of the signal. `How many unique locations within the bounds of the map contain an antinode?`

# Kiwi_the_first Disk Fragmenter

Another push of the button leaves you in the familiar hallways of some friendly `amphipods`! Good thing you each somehow got your own personal mini submarine. The Historians jet away in search of the Chief, mostly by driving directly into walls.

While The Historians quickly figure out how to pilot these things, you notice an amphipod in the corner struggling with his computer. He's trying to make more contiguous free space by compacting all of the files, but his program isn't working; you offer to help.

He shows you the `disk map` (your puzzle input) he's already generated. For example:

```plaintext
2333133121414131402
```

The disk map uses a dense format to represent the layout of `files` and `free space` on the disk. The digits alternate between indicating the length of a file and the length of free space.

So, a disk map like `12345` would represent a one-block file, two blocks of free space, a three-block file, four blocks of free space, and then a five-block file. A disk map like `90909` would represent three nine-block files in a row (with no free space between them).

Each file on disk also has an `ID number` based on the order of the files as they appear before they are rearranged, starting with ID `0`. So, the disk map `12345` has three files: a one-block file with ID `0`, a three-block file with ID `1`, and a five-block file with ID `2`. Using one character for each block where digits are the file ID and `.` is free space, the disk map `12345` represents these individual blocks:

```plaintext
0..111....22222
```

The first example above, `2333133121414131402`, represents these individual blocks:

```plaintext
00...111...2...333.44.5555.6666.777.888899
```

The amphipod would like to `move file blocks one at a time` from the end of the disk to the leftmost free space block (until there are no gaps remaining between file blocks). For the disk map `12345`, the process looks like this:

```plaintext
0..111....22222
02.111....2222.
022111....222..
0221112...22...
02211122..2....
022111222......
```

The first example requires a few more steps:

```plaintext
00...111...2...333.44.5555.6666.777.888899
009..111...2...333.44.5555.6666.777.88889.
0099.111...2...333.44.5555.6666.777.8888..
00998111...2...333.44.5555.6666.777.888...
009981118..2...333.44.5555.6666.777.88....
0099811188.2...333.44.5555.6666.777.8.....
009981118882...333.44.5555.6666.777.......
0099811188827..333.44.5555.6666.77........
00998111888277.333.44.5555.6666.7.........
009981118882777333.44.5555.6666...........
009981118882777333644.5555.666............
00998111888277733364465555.66.............
0099811188827773336446555566..............
```

The final step of this file-compacting process is to update the `filesystem checksum`. To calculate the checksum, add up the result of multiplying each of these blocks' position with the file ID number it contains. The leftmost block is in position `0`. If a block contains free space, skip it instead.

Continuing the first example, the first few blocks' position multiplied by its file ID number are `0 * 0 = 0`, `1 * 0 = 0`, `2 * 9 = 18`, `3 * 9 = 27`, `4 * 8 = 32`, and so on. In this example, the checksum is the sum of these, `1928`.

Compact the amphipod's hard drive using the process he requested. `What is the resulting filesystem checksum?` (Be careful copy/pasting the input for this puzzle; it is a single, very long line.)
