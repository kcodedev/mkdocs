# Text Processing

## cat
Concatenate and display files.

- `cat file.txt` : Display file contents
- `cat file1.txt file2.txt` : Concatenate files

## less
View file contents page by page.

- `less file.txt` : View file with navigation

## head
Display first lines of a file.

- `head file.txt` : First 10 lines
- `head -n 20 file.txt` : First 20 lines

## tail
Display last lines of a file.

- `tail file.txt` : Last 10 lines
- `tail -f file.txt` : Follow file (real-time)

## grep
Search for patterns in files.

- `grep "pattern" file.txt` : Search for pattern
- `grep -r "pattern" directory/` : Recursive search
- `grep -i "pattern" file.txt` : Case-insensitive

## sed
Stream editor for text manipulation.

- `sed 's/old/new/g' file.txt` : Replace text
- `sed -i 's/old/new/g' file.txt` : In-place edit

## awk
Pattern scanning and processing language.

- `awk '{print $1}' file.txt` : Print first column
- `awk '/pattern/ {print}' file.txt` : Print lines matching pattern

## cut
Remove sections from lines of files.

- `cut -d',' -f1 file.csv` : Cut first field (comma-separated)

## sort
Sort lines of text files.

- `sort file.txt` : Sort alphabetically
- `sort -n file.txt` : Sort numerically

## uniq
Report or omit repeated lines.

- `uniq file.txt` : Remove duplicate lines
- `uniq -c file.txt` : Count occurrences

## wc
Print newline, word, and byte counts.

- `wc file.txt` : Count lines, words, bytes
- `wc -l file.txt` : Count lines only